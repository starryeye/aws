## Subnet

- VPC 내부의 네트워크 구역
    - EC2, RDS 등 리소스를 배치하는 공간

---

- 특징
    - 하나의 Subnet은 하나의 AZ에 속함
    - VPC의 IP 범위를 나눠서 사용
    - 실제 서버가 배치되는 위치

---

## 핵심 개념

- Subnet 자체는 "Public / Private" 속성이 없음
- Public / Private 여부는 "Route Table"로 결정됨

---

## 유형

### Public Subnet

- 정의
    - 인터넷과 직접 연결된 Subnet

- 조건

    - Route Table에 다음이 있어야 함

      0.0.0.0/0 → Internet Gateway (IGW)

    - EC2에 Public IP 필요

---

### Private Subnet

- 정의
    - 인터넷에서 직접 접근 불가능한 Subnet

- 조건

    - IGW로 가는 라우트 없음

- (옵션) 인터넷 "나가기만" 가능

  0.0.0.0/0 → NAT Gateway

---

## 핵심 비교

| 구분 | Public Subnet | Private Subnet |
|---|---|---|
외부(인터넷)에서 접근 | ⭕ 가능 | ❌ 불가 |
IGW 연결 | ⭕ 있음 | ❌ 없음 |
NAT 사용 | 필요 없음 | outbound 시 필요 |
사용 용도 | ALB, Bastion | EC2, RDS |

---

## 구조 예시

    VPC (10.0.0.0/16)

    ├── Public Subnet (10.0.1.0/24)
    │     → ALB, NAT Gateway
    │
    ├── Private Subnet (10.0.2.0/24)
    │     → EC2 (Backend)
    │
    └── Private Subnet (10.0.3.0/24)
          → RDS

---

## 핵심 정리

- Subnet = "리소스를 배치하는 네트워크 영역"
- Public / Private는 "라우팅으로 결정됨"

---

## 한 줄 요약

- Subnet = "서버를 어디에 둘지 결정하는 네트워크 공간"