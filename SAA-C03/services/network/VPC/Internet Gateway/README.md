## Internet Gateway (IGW)

- VPC 를 인터넷과 연결해주는 게이트웨이
    - VPC 내부 리소스가 인터넷과 통신할 수 있도록 함

---

- 특징
    - 완전 관리형
    - 수평 확장 가능 (고가용성)
    - VPC에 하나만 연결 가능

---

- 역할

    - 인터넷 → VPC (Inbound)
    - VPC → 인터넷 (Outbound)

---

## 동작 조건

IGW 만 있다고 인터넷이 되는 것이 아님

다음 조건이 모두 필요

- IGW가 VPC에 연결되어 있어야 함

- Route Table 설정
  - 0.0.0.0/0 → IGW

- EC2 에 Public IP 필요

---

## 동작 흐름

    Client → Internet → IGW → VPC → EC2

    EC2 → IGW → Internet

---

## 특징 정리

- 양방향 통신 가능 (Inbound / Outbound)
- Public Subnet에서 사용
- Private Subnet 에서는 직접 사용하지 않음

---

## IGW vs NAT Gateway

| 구분 | IGW | NAT Gateway |
|---|---|---|
방향 | 양방향 | Outbound only |
사용 대상 | Public Subnet | Private Subnet |
Public IP 필요 | ⭕ | NAT에만 필요 |

---

## 사용 케이스

- 웹 서버 (ALB, EC2)
- Bastion Host
- 인터넷 접근이 필요한 서비스

---

## 한 줄 정리

- IGW = "VPC와 인터넷을 연결하는 양방향 게이트"

---

- 참고

    - Public Subnet 필수 구성 요소
      - VPC 는 원래 외부 인터넷과 소통할 수 없는 독립적으로 분리된 네트워크인데.. 
      - 특정 Subnet 에 IGW 를 사용함으로써 인터넷과 양방향 통신이되고 
      - 이를 public Subnet 이라 한다. 
    - Route Table과 함께 동작