# EKS 기반 데이터 워크로드 플랫폼

> Spark Driver와 Executor를 Kubernetes Pod로 실행하고, 작업 제출부터 Scheduling과 Node 공급, 실행 결과 확인까지 이어지는 환경을 구성했습니다.

## 요약

| 항목 | 내용 |
|---|---|
| 기간 | 2024.12 ~ 2025.12 |
| 담당 | EKS와 EMR on EKS 기반 Spark 실행 인프라 구성 |
| 기술 | EKS, EMR on EKS, Kubernetes, Airflow, YuniKorn, Karpenter, Terraform, Helm, Datadog |
| 결과 | 플랫폼 비용 약 30% 절감, Spark 처리 시간 약 20~30% 개선 |

## 배경

Spark 실행 위치를 Databricks에서 EMR on EKS로 옮기면서 Spark 설정뿐 아니라 Pod Scheduling, Node 생성, Resource Request와 모니터링을 함께 정리해야 했습니다.

## 플랫폼 구성

![EKS 기반 워크로드 플랫폼](../assets/cloud-native-spark-platform-components-redacted.png)

| 구분 | 구성요소 | 역할 |
|---|---|---|
| Orchestration | Airflow | Glue, EMR on EKS와 SageMaker 작업 실행 |
| Runtime | EMR Virtual Cluster | EKS에서 Spark Driver와 Executor 실행 |
| Scheduling | YuniKorn, Default Scheduler | Spark와 일반 Pod의 배치 기준 분리 |
| Node Scaling | Karpenter, Cluster Autoscaler | Pod 조건에 맞는 Node 공급 |
| Pod Scaling | KEDA, Metrics Server | Event와 Metric 기반 Application 확장 |
| Networking | AWS Load Balancer Controller | EKS Application의 Load Balancer 연결 |
| Observability | Spark History Server, Datadog | Application과 Kubernetes 상태 확인 |
| Infrastructure | EKS, Terraform, Helm | Cluster와 구성요소 관리 |

## 실행 흐름

    Airflow Task
      → EMR Virtual Cluster에 Job 제출
      → Spark Driver Pod 생성
      → YuniKorn Queue에서 Resource 확인
      → Karpenter가 Node 준비
      → Executor Pod 생성
      → Spark Job 실행
      → Spark History Server와 Datadog 확인

## 맡았던 일

- EMR Virtual Cluster와 Spark 실행 환경 구성
- Driver·Executor Resource와 Pod Template 정리
- YuniKorn Queue와 Kubernetes Default Scheduler 구성
- Spark 작업 특성에 맞는 Karpenter NodePool 구성
- AWS Load Balancer Controller, KEDA와 Metrics Server 운영
- Terraform과 Helm 기반 구성 관리

## 작업이 시작되지 않을 때

1. Airflow가 Job을 정상 제출했는지 확인했습니다.
2. Driver Pod Event와 Resource Request를 확인했습니다.
3. YuniKorn Queue와 Scheduling 상태를 확인했습니다.
4. Karpenter가 조건에 맞는 Node를 만들 수 있는지 확인했습니다.
5. Application이 시작된 뒤에는 Spark Job과 Stage를 확인했습니다.

작업이 늦게 시작될 때 Spark 설정부터 바꾸지 않았습니다. 제출, Scheduling, Node 공급과 Application 실행을 나눠 원인을 확인했습니다.

## 결과

- 기존 환경보다 플랫폼 비용을 약 30% 줄였습니다.
- Spark 처리 시간은 작업에 따라 약 20~30% 개선했습니다.
- Scheduling, Node 공급과 Spark 실행 문제를 나눠 확인하는 기준을 정리했습니다.

