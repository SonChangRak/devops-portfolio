# MLOps 실행·배포 흐름

> Airflow에서 Feature 생성, SageMaker 학습과 평가, Model Registry 등록과 Endpoint 변경을 실행하고, 필요한 코드와 Container Image를 S3와 ECR로 전달했습니다.

## DevOps 관점에서 맡은 범위

이 작업에서 맡은 부분은 모델을 설계하는 일이 아니었습니다. ML 작업이 정해진 순서로 실행되고, 평가 결과를 확인한 뒤 배포되며, 실패한 단계와 사용한 Artifact를 찾을 수 있는 구조를 만드는 일이었습니다.

## 전체 구성

![ML 워크로드 실행과 배포](../assets/mlops-lifecycle-airflow-sagemaker.png)

    Feature / Training / Evaluation
      Airflow
        → EMR on EKS에서 Spark Feature 생성
        → SageMaker Feature Store 적재
        → SageMaker Training Job
        → SageMaker Processing Job 평가
        → 평가 결과에 따른 후속 Task 분기

    Model / Endpoint
      Model Registry 등록
        → SageMaker Model 생성
        → Endpoint Configuration 생성
        → 기존 Endpoint 변경

    Artifact Delivery
      Evaluation Repository → GitLab Runner → S3
      Inference Repository → GitLab Runner → ECR

## 실행 단계를 분리한 이유

Training Job이 성공했다고 바로 Endpoint를 변경하지 않았습니다. Processing Job에서 평가 코드를 실행하고 Metric을 확인한 뒤, 배포가 필요한 경우에만 Model Registry 이후 단계를 진행하도록 했습니다.

Feature, 학습, 평가, 등록과 Endpoint 변경을 별도 Airflow Task로 나눠 실패 위치를 확인할 수 있게 했습니다.

## 배포 Artifact

평가 코드는 GitLab Workflow를 통해 S3에 배포하고, Inference Image는 GitLab Runner에서 Build해 ECR에 저장했습니다.

실행 환경마다 Source를 다시 Build하지 않고, S3의 평가 코드와 ECR의 Container Image를 배포 단위로 사용했습니다. ML 작업 실행과 Artifact 준비를 분리해 각각의 변경 위치를 확인할 수 있도록 했습니다.

## 맡았던 일

- Feature 생성부터 Endpoint 변경까지 Airflow DAG 구성
- EMR on EKS와 SageMaker Feature Store 연결
- Training Job과 Processing Job 실행 구성
- 평가 결과 확인과 후속 Task 분기
- Model Registry, Model, Endpoint Configuration과 Endpoint 작업 구성
- 평가 코드와 Inference Image 배포 흐름 연결

## 실패 지점

| 단계 | 확인할 위치 |
|---|---|
| Feature | Airflow Task, EMR on EKS Job, Feature Store 적재 상태 |
| Training | SageMaker Training Job Log, Input Feature |
| Evaluation | Processing Job Log, S3 Evaluation Code, Output Metric |
| Registry | Model Registry 권한, Model Package 정보 |
| Deploy | ECR Image, SageMaker Model, Endpoint Configuration |
| Runtime | EKS Application Log, SageMaker Endpoint 상태, Network 연결 |

## EKS Application과 Endpoint

![EKS Application과 SageMaker Endpoint](../assets/eks-application-delivery-redacted.png)

Model Endpoint를 배포하는 흐름뿐 아니라, 환경별 EKS Application이 ALB를 통해 요청을 받고 OpenSearch, SageMaker Endpoint와 ElastiCache를 사용하는 런타임 구조도 다뤘습니다.

## 정리

MLOps 경험은 DevOps 포트폴리오에서 별도 기술 영역으로 과장하지 않았습니다. 기존의 Container Image 배포, Workflow 관리, 로그 확인과 장애 지점 분리 경험을 ML 워크로드에 적용한 사례로 정리했습니다.

