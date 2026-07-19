# Cloud·On-Premise 환경과 자산 관리

> AWS Data Lake, EMR, Databricks와 On-Premise Hadoop/Spark 환경을 운영하면서 실행 인프라와 Cloud 자산을 함께 관리했습니다.

## 분석 인프라의 변화

### AWS Data Lake와 EMR

- Adjust API, MongoDB Atlas와 RDS 데이터를 S3에 적재
- EMR on EC2와 SageMaker Notebook Instance 기반 분석 환경 구성
- EC2 기반 Airflow 설치와 운영
- CloudFormation 기반 EMR 생성과 설정 관리
- CloudWatch 기반 서버 상태 확인
- Active Directory 기반 사용자 관리 연동

### Databricks

- Workspace와 접근 프로세스 구성
- Cluster Spec과 Cluster Policy 구성
- 서비스 계정 Token을 Secrets Manager에서 관리
- Okta 기반 사용자 연동
- Spot Instance 사용을 위한 AWS Service Quotas 관리

### On-Premise Hadoop/Spark

- Hadoop과 Spark 환경 설계·구축
- Delta OSS 기반 데이터 사용 방식 검토
- Hive, Zeppelin과 JupyterHub 구성
- Cloud와 On-Premise를 함께 사용하는 분석 환경 기반 마련

이 과정에서 Managed Service와 직접 운영하는 환경의 차이, 사용자 접근과 인증, 비용과 운영 범위를 함께 경험했습니다.

## Cloud 자산 관리

환경과 Resource가 늘어나면서 Cloud 자산을 같은 기준으로 수집하고 관리할 필요가 있었습니다.

    CloudQuery
      → AWS 자산 수집
      → PostgreSQL 저장
      → NetBox 관리
      → Grafana 확인

### 맡았던 일

- CloudQuery를 이용한 Cloud 자산 수집
- PostgreSQL에 자산 정보 저장
- NetBox에서 자산 정보 관리
- Airflow DAG로 수집과 CRUD 작업 실행
- Secrets Manager에서 Database와 API Token 관리
- Grafana에서 자산 현황 확인

자산 관리 시스템은 ISMS-P 심사에 필요한 자산 정보와 비용·장애 확인에 사용할 데이터를 한곳에 모으기 위해 만들었습니다.

## DevOps 업무와 연결되는 부분

단일 EKS Cluster만 운영한 경험이 아니라 AWS Managed Service, VM 기반 환경, On-Premise Hadoop/Spark와 Kubernetes 환경을 비교하며 운영했습니다. Application 개발 경험도 있어 Runtime에서 Database, Search, Cache와 외부 Endpoint가 어떻게 연결되는지 함께 확인할 수 있었습니다.

