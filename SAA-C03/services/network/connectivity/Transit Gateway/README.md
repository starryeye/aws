## Transit Gateway (TGW)

- 여러 VPC와 온프레미스를 하나의 중앙 허브로 연결하는 네트워크 서비스

---

## 핵심 개념

- Hub-and-Spoke 구조
- 중앙 라우터 역할

---

## 특징

    - VPC 다수 연결 가능
    - Site-to-Site VPN / Direct Connect 연결 가능
    - 중앙에서 라우팅 관리
    - 확장성 매우 높음

---

## 동작 구조

        VPC A
           \
        VPC B ——— Transit Gateway ——— On-Premises
           /
        VPC C

---

## 구성 요소

### 1️⃣ Transit Gateway

- 중앙 허브 역할

---

### 2️⃣ Attachment

- VPC / VPN / Direct Connect 연결 지점

---

### 3️⃣ Route Table

- TGW 내부 라우팅 관리

---

## 특징 정리

- VPC 간 연결을 중앙에서 관리
- 네트워크 복잡도 감소
- Peering보다 확장성 우수

---

## VPC Peering vs Transit Gateway

| 구분 | VPC Peering | Transit Gateway |
|---|---|---|
구조 | 1:1 연결 | Hub-and-Spoke |
확장성 | 낮음 | 매우 높음 |
관리 | 복잡 | 중앙 집중 |
Transitive Routing | ❌ | ⭕ |

---

## 사용 케이스

- 다수 VPC 연결
- 대규모 네트워크 아키텍처
- 온프레미스 + 여러 VPC 통합

---

## 한 줄 정리

- Transit Gateway = "여러 VPC 와 온프레미스를 연결하는 중앙 라우터"


--- 

## VPC Peering vs Transit Gateway vs PrivateLink

| 구분 | VPC Peering | Transit Gateway | PrivateLink |
|---|---|---|---|
연결 대상 | VPC ↔ VPC | 여러 VPC + 온프레미스 | 특정 서비스 |
연결 방식 | 1:1 직접 연결 | Hub-and-Spoke | Interface Endpoint |
구조 | Mesh | 중앙 허브 | 서비스 단위 |
통신 범위 | 전체 VPC | 전체 VPC | 특정 서비스만 |
IP 통신 | Private IP | Private IP | Private IP |
Transitive Routing | ❌ | ⭕ | ❌ |
CIDR(IP 주소 범위) 충돌 | ❌ 불가 | ⭕ 가능 | ⭕ 가능 |
확장성 | 낮음 | 매우 높음 | 높음 |
보안 | 중간 | 중간 | 매우 높음 |
관리 | 복잡 (많아질수록) | 중앙 관리 | 단순 |
대표 용도 | VPC 2개 연결 | 대규모 네트워크 | 서비스 공유 |

---

## 핵심 감각

- VPC Peering = "VPC를 직접 연결"
- Transit Gateway = "중앙 라우터로 연결"
- PrivateLink = "서비스만 연결"

---

## 시험 한 줄 정리

```text
Peering → 1:1 VPC 연결
TGW → 여러 VPC 연결 (hub)
PrivateLink → 특정 서비스 연결