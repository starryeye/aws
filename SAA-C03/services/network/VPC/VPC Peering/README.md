## VPC Peering

- 두 VPC를 직접 연결하여 Private IP로 통신할 수 있게 해주는 서비스

---

## 핵심 개념

- VPC ↔ VPC 네트워크를 직접 연결
- 인터넷, NAT, IGW 없이 통신 가능

---

## 특징

    - Private IP 통신 ⭕
    - 인터넷 경유 ❌
    - 완전 관리형
    - 양방향 통신 가능

---

## 동작 방식

    VPC A  ←→  VPC B
       (Private IP 통신)

---

## 구성 조건

### 1️⃣ Peering 연결 생성

- VPC A ↔ VPC B 연결 요청 / 승인

---

### 2️⃣ Route Table 설정 (양쪽 모두)

    VPC A → VPC B CIDR → Peering Connection
    VPC B → VPC A CIDR → Peering Connection

---

### 3️⃣ Security Group / NACL 허용

---

## 핵심 제약

### CIDR 겹치면 ❌

- 두 VPC의 IP 대역이 겹치면 Peering 불가

---

### Transitive Routing ❌

- A ↔ B, B ↔ C 연결되어 있어도
- A ↔ C 자동 연결 안됨

---

## 특징 정리

- 전체 네트워크 연결
- 단순하고 빠름
- 설정 간단

---

## 사용 케이스

- VPC 간 내부 서비스 통신
- 계정 간 네트워크 연결
- 마이크로서비스 간 통신

---

## VPC Peering vs PrivateLink

| 구분 | VPC Peering | PrivateLink |
|---|---|---|
연결 범위 | VPC 전체 | 특정 서비스 |
보안 | 낮음 | 높음 |
CIDR 충돌 | 불가 | 가능 |
구조 | 네트워크 연결 | 서비스 연결 |

---

## VPC Peering vs NAT

| 구분 | VPC Peering | NAT Gateway |
|---|---|---|
통신 대상 | 다른 VPC | 인터넷 |
경로 | 내부 | 인터넷 |
보안 | 높음 | 낮음 |

---

## 한 줄 정리

- VPC Peering = "두 VPC를 하나의 네트워크처럼 연결"