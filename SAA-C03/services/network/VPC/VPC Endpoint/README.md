## VPC Endpoint

- VPC 내부에서 인터넷을 거치지 않고 AWS 서비스에 접근할 수 있게 해주는 서비스
- VPC A 에서 VPC B 가 있는데..
    - VPC A 에서 VPC B 에 존재하는 어떤 AWS 서비스에 인터넷 경유 없이 접근하고 싶을 때 사용한다.
    - VPC Endpoint(VPC B 연결점) 는 VPC A 에 존재하게 된다.
---

## 핵심 개념

- Private Subnet → AWS 서비스(S3, DynamoDB 등) 직접 접근 가능
- NAT / IGW 필요 없음

---

## 특징
    - 인터넷 경유 ❌
    - AWS 내부 네트워크로 통신
    - 보안 강화 (외부 노출 없음)
    - 비용 절감 (NAT Gateway 비용 절약 가능)

---

## 유형

### 1️⃣ Gateway VPC Endpoint

- 대상 서비스
    - S3
    - DynamoDB

- 특징
    - Route Table에 추가
    - 무료

---

### 2️⃣ Interface VPC Endpoint (=PrivateLink)

- 대상 서비스
    - 대부분 AWS 서비스 (SQS, SNS, EC2 API 등)
    - SaaS / 다른 VPC 서비스

- 특징
    - ENI (Elastic Network Interface) 생성
    - Private IP로 접근
    - 비용 발생

---

## 동작 방식

### Gateway Endpoint (Gateway VPC Endpoint)

    Private Subnet → Route Table → S3 / DynamoDB

---

### Interface Endpoint (Interface VPC Endpoint)

    Private Subnet → ENI → AWS 서비스

---

## NAT vs VPC Endpoint

| 구분 | NAT Gateway | VPC Endpoint |
|---|---|---|
경로 | 인터넷 경유 | AWS 내부 |
보안 | 낮음 | 높음 |
비용 | 높음 | 낮음 (Gateway 무료) |
대상 | 모든 인터넷 | 특정 AWS 서비스 |

---

## 사용 케이스

- Private Subnet에서 S3 접근
- NAT 비용 절감
- 보안 요구 높은 환경

---

## 한 줄 정리

- VPC Endpoint = "인터넷 없이 AWS 서비스에 접근하는 전용 통로"