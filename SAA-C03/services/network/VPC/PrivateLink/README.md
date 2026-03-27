## AWS PrivateLink

- VPC 간 또는 AWS 서비스에 대해
  인터넷 없이 Private IP로 통신할 수 있게 해주는 서비스

---

## 핵심 개념

- 특정 서비스만 Private 하게 연결
- AWS VPC Endpoint 의 Interface Endpoint 기반이다.
- ENI 를 통해 Private IP 로 접근

---

## 특징

    - 인터넷 경유 ❌
    - Private IP 통신 ⭕
    - 보안 강화
    - 다른 VPC / 계정 / SaaS 연결 가능

---

## 구성 요소

### 1️⃣ Service Provider (서비스 제공자)

- 서비스를 제공하는 쪽 (Provider VPC)
- 일반적으로 NLB 뒤에 서비스 구성

---

### 2️⃣ Endpoint Service

- Provider VPC 에서 서비스를 PrivateLink 로 노출

---

### 3️⃣ Interface Endpoint (Consumer)

- Consumer VPC에 생성됨
- 생성 시 ENI가 함께 생성됨
- Private IP를 통해 서비스 접근 가능

---

## ENI 개념 (핵심)

- ENI 는 Consumer VPC 내부에 생성됨
- Interface Endpoint 생성 시 자동으로 생성됨

---

## 동작 흐름

    Consumer VPC
        EC2 → ENI (Interface Endpoint, Private IP)
                    ↓
            AWS 내부 네트워크
                    ↓
    Provider VPC (서비스, NLB 뒤)

---

## 핵심 이해

- ENI = Consumer VPC 내부의 "서비스 접근 지점"
- 마치 "내 VPC 안에 서비스가 있는 것처럼 동작"

---

## VPC Endpoint vs PrivateLink

| 구분 | VPC Endpoint | PrivateLink |
|---|---|---|
개념 | AWS 서비스 접근 | 서비스 간 연결 |
유형 | Gateway / Interface | Interface 기반 |
대상 | S3, DynamoDB 등 | VPC / SaaS |

---

## VPC Peering vs PrivateLink

| 구분 | VPC Peering | PrivateLink |
|---|---|---|
연결 범위 | VPC 전체 | 특정 서비스만 |
보안 | 낮음 | 높음 |
CIDR 충돌 | 문제 있음 | 문제 없음 |

---

## NAT vs PrivateLink

| 구분 | NAT Gateway | PrivateLink |
|---|---|---|
경로 | 인터넷 | AWS 내부 |
보안 | 낮음 | 높음 |
대상 | 모든 인터넷 | 특정 서비스 |

---

## 사용 케이스

- 다른 VPC 서비스 접근 (Peering 없이)
- SaaS 서비스 연결
- 내부 API 서비스 공유
- 보안 요구 높은 환경

---

## 한 줄 정리

- PrivateLink = "특정 서비스만 Private하게 연결하는 구조"