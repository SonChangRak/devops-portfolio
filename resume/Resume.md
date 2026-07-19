# 손창락

## DevOps Engineer | Data & AI Platform

- Email: thsckdfkr@gmail.com
- 지원 분야: DevOps Engineer / Platform Engineer / Cloud Platform Engineer
- 출근 가능: 오퍼 확정 후 4주 이내

## 소개

시스템 운영으로 일을 시작해 Backend 개발을 경험했고, 현재는 AWS와 Kubernetes 기반 데이터 플랫폼 인프라를 담당하고 있습니다.

EKS에서 Airflow와 Spark Application이 실행되는 환경을 구성했고, YuniKorn과 Karpenter로 워크로드 배치와 Node 확장을 관리했습니다. Terraform과 Helm으로 Infrastructure와 Kubernetes Application의 변경 범위를 나누고, GitLab Runner와 ECR을 이용해 Lambda와 EKS Application을 배포했습니다.

최근에는 Airflow와 SageMaker를 연결해 ML 학습·평가·배포 흐름을 구성하고, 반복적으로 확인하던 Spark 실행 이력을 EventBridge, Lambda와 Bedrock 모델을 이용해 리포트로 정리했습니다.

## 주요 경험과 결과

- Databricks 기반 Spark 환경을 EMR on EKS로 전환해 플랫폼 비용을 약 30% 줄였습니다.
- Kubernetes 기반 실행 환경에서 Spark 처리 시간을 작업에 따라 약 20~30% 개선했습니다.
- Terraform과 Helm으로 AWS Resource와 Kubernetes 구성을 관리했습니다.
- GitLab Runner와 ECR 기반 Lambda·EKS Application 배포 흐름을 구성했습니다.
- Spark History Server, Datadog, Grafana와 CloudWatch 기반 운영 확인 환경을 구성했습니다.
- Airflow에서 SageMaker Training·Evaluation·Model Registry·Endpoint 변경까지 실행하도록 구성했습니다.
- CloudQuery, PostgreSQL, NetBox와 Grafana를 연결한 Cloud 자산 관리 환경을 만들었습니다.

## 기술

| 구분 | 기술 |
|---|---|
| Cloud | AWS, EKS, EC2, S3, EMR, Lambda, EventBridge, DynamoDB, ECR, CloudWatch |
| Kubernetes | Kubernetes, Docker, Helm, Karpenter, YuniKorn, KEDA, Cluster Autoscaler, AWS Load Balancer Controller |
| IaC / Delivery | Terraform, CloudFormation, GitLab CI/CD, GitLab Runner, Shell Script, ECR, Container Image |
| Observability | Datadog, Grafana, CloudWatch, Spark History Server, Splunk |
| Data / AI Workload | Spark, Airflow, Databricks, SageMaker, Glue, Athena, Amazon Bedrock, n8n |
| Development | Python, Java, Spring Boot, Node.js, PostgreSQL, MySQL, Elasticsearch, OpenSearch |

## 경력

### 웍스피어(구 잡코리아)

**2022.01.17 ~ 재직 중 | 매니저 | 데이터 플랫폼 인프라 구축 및 운영**

- EKS에서 Airflow, EMR on EKS Spark Application과 데이터 플랫폼 구성요소가 실행되는 환경을 구축·운영했습니다.
- Spark Driver와 Executor Resource, YuniKorn Scheduling과 Karpenter Node 확장 흐름을 구성했습니다.
- Terraform으로 AWS Resource를 관리하고 Helm으로 Kubernetes Application과 설정을 배포했습니다.
- GitLab Runner에서 Container Image를 Build해 ECR에 저장하고 Lambda와 환경별 EKS Application에 배포하도록 구성했습니다.
- AWS Load Balancer Controller, Cluster Autoscaler, KEDA와 Metrics Server를 운영했습니다.
- Spark History Server, Datadog, Grafana와 CloudWatch에서 작업 실패와 리소스 사용 상태를 확인했습니다.
- Airflow와 SageMaker를 연결해 Feature 생성, 학습, 평가, Model Registry 등록과 Endpoint 변경을 실행하도록 구성했습니다.
- CloudQuery, PostgreSQL, NetBox와 Grafana 기반 자산 관리 시스템을 구축해 ISMS-P 대응과 비용·장애 확인에 활용했습니다.

### 에이치엔아이엔씨

**2021.09.01 ~ 2022.01.07 | 대리 | 모바일 애플리케이션 및 관리자 웹 개발**

- React Native 기반 신원 인증 앱과 Thymeleaf 관리자 웹을 개발했습니다.
- Android Java와 iOS Swift로 자체 SDK를 수정하고 유지보수했습니다.

### 비플라이소프트

**2020.04.06 ~ 2021.08.31 | 프로 | 로제우스 뉴스 앱 Backend 개발**

- Spring Boot 기반 REST API와 Python 뉴스 Crawler를 개발했습니다.
- Elasticsearch 기반 뉴스 저장·검색 환경과 문서 유사도 모듈을 만들었습니다.

### 더유니파이

**2018.03.05 ~ 2020.04.03 | 과장 | 웹 애플리케이션 및 Backend 개발**

- Spring과 전자정부프레임워크를 이용해 REST API와 관리자 웹을 개발했습니다.
- 택시운전자 앱, 재난안전통신망 ITSM, 자율주행 Dashboard 등 고객사 프로젝트에 참여했습니다.

### 티이에이

**2017.08.01 ~ 2018.02.28 | 주임 | 시스템 운영 및 Splunk 유지보수**

- 고객사 웹 Dashboard와 Splunk 기반 로그 수집·분석 환경을 유지보수했습니다.
- 로그를 조회해 시스템 상태와 장애 원인을 확인했습니다.

## 경력 이동 배경

| 시기 | 이동 | 배경 |
|---|---|---|
| 2018.02 | 티이에이 → 더유니파이 | 회사 인수합병 후 같은 조직에서 근무를 이어가며 시스템 운영에서 Backend 개발로 업무를 넓혔습니다. |
| 2020.04 | 더유니파이 → 비플라이소프트 | 고객사 프로젝트에서 B2C 서비스와 데이터 수집·검색 영역으로 경험을 넓혔습니다. |
| 2021.09 | 비플라이소프트 → 에이치엔아이엔씨 | Backend에서 모바일 앱과 SDK까지 서비스 영역을 확장했습니다. |
| 2022.01 | 에이치엔아이엔씨 → 잡코리아 | 애플리케이션 개발 경험을 바탕으로 인프라와 데이터 플랫폼 운영을 중심으로 커리어를 정리했습니다. |
| 현재 | 다음 회사 검토 | AWS와 Kubernetes 기반 데이터·AI 워크로드 운영 경험을 더 큰 규모의 플랫폼 자동화와 안정성 개선 업무로 확장하려 합니다. |

## 학력·교육·자격

- 용인대학교 컴퓨터과학과 졸업, 2011.03 ~ 2018.08
- 쌍용교육센터 Framework를 활용한 빅데이터 전문가 과정, 2017.01.09 ~ 2017.06.23, 960시간
- 정보처리기사, 한국산업인력공단, 2021.08.20
- 병역: 육군 병장 만기전역, 2011.12.13 ~ 2013.09.12

## Portfolio

- [EKS 기반 데이터 워크로드 플랫폼](../portfolio/01_EKS_Workload_Platform.md)
- [Terraform·Helm·GitLab 기반 배포 환경](../portfolio/02_IaC_and_Delivery.md)
- [Observability와 운영 자동화](../portfolio/03_Observability_and_Operations.md)
- [MLOps 실행·배포 흐름](../portfolio/04_MLOps_Operations.md)
- [Cloud·On-Premise 환경과 자산 관리](../portfolio/05_Hybrid_Cloud_and_Assets.md)

