## VPC (Virtual Private Cloud)

- AWS에서 제공하는 가상 네트워크
    - 사용자가 직접 네트워크 환경을 설계

---

- 특징
    - 완전 격리된 네트워크
        - 다른 VPC와 기본적으로 통신 불가
    - IP 주소 범위 지정 (CIDR)
        - 예: 10.0.0.0/16
    - 네트워크 구성 요소 포함
        - Subnet, Route Table, Gateway 등

---

- 구성 요소

    - Subnet
        - VPC 내부 네트워크 분할

    - Route Table
        - 트래픽 경로 정의

    - Internet Gateway (IGW)
        - 인터넷 연결

    - NAT Gateway
        - Private → Internet 요청 가능 (Outbound only)

    - Security Group / NACL
        - 보안 제어

---

- 특징 요약

    - Region 단위 리소스
    - AZ를 포함하는 개념 (VPC ⊃ AZ)
    - 네트워크의 "틀"

---

## 한 줄 정리

- VPC = "AWS 안에 만드는 나만의 네트워크"

---

## 네트워크 연결 방식 비교

| 구분 | NAT Gateway | VPC Endpoint | PrivateLink | VPC Peering |
|---|---|---|---|---|
목적 | 인터넷 접근 | AWS 서비스 접근 | 서비스 간 연결 | VPC 간 연결 |
통신 대상 | 인터넷 | S3, DynamoDB 등 | 특정 서비스 | 다른 VPC |
경로 | 인터넷 경유 | AWS 내부 | AWS 내부 | AWS 내부 |
방향 | Outbound only | 양방향 | 양방향 | 양방향 |
연결 범위 | 전체 인터넷 | 특정 AWS 서비스 | 특정 서비스 | VPC 전체 |
보안 | 낮음 | 높음 | 매우 높음 | 중간 |
CIDR 충돌 | 없음 | 없음 | 없음 | 불가 |
대표 특징 | Private → Internet | NAT 대체 | 서비스 단위 연결 | 네트워크 전체 연결 |

---

## 핵심 감각

- NAT Gateway = "인터넷으로 나가는 출구"
- VPC Endpoint = "AWS 서비스로 가는 내부 통로"
- PrivateLink = "특정 서비스만 Private하게 연결", VPC Endpoint 의 일종이다.
- VPC Peering = "VPC 전체를 연결"

---

## 시험용 한 줄 비교

```text
NAT = 인터넷
Endpoint = AWS 서비스
PrivateLink = 서비스 연결
Peering = VPC 연결