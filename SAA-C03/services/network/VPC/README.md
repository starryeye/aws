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
        - Private → Internet 통신

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