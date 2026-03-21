## NAT Gateway

- Private Subnet 에서
  인터넷 방향으로 "outbound 요청을 보낼 수 있도록" 해주는 서비스
  - 인터넷에서 private subnet 방향으로의 접근은 여전히 불가능하다.

---

- 특징
    - Outbound only (단방향)
    - 외부에서 직접 접근 불가 (Inbound ❌)
    - 완전 관리형 (고가용성)
    - Public Subnet에 위치해야 함
    - Elastic IP 필요

---

## 역할

- Private → Internet 요청 가능 ⭕
- Internet → Private 직접 접근 ❌

---

## 동작 방식

    private subnet 영역 [Private EC2] → (요청) → public subnet 영역 [NAT] → private/public subnet 포함하는 VPC 영역[IGW] → Internet
                              ↓
                        (응답은 다시 돌아옴)

---

## 핵심 개념

- "요청 기반 응답만 허용"

  → 내부에서 먼저 요청해야만 응답 가능

---

## 동작 조건

### 1️⃣ NAT Gateway는 Public Subnet에 위치

### 2️⃣ NAT Gateway에 Elastic IP 할당

### 3️⃣ Private Subnet Route Table

    0.0.0.0/0 → NAT Gateway

### 4️⃣ Public Subnet에는 IGW 연결 필요

---

## IGW vs NAT Gateway

| 구분 | IGW | NAT Gateway |
|---|---|---|
방향 | 양방향 | Outbound only |
접근 방식 | 누구나 접근 가능 | 내부 요청 기반 |
위치 | VPC | Public Subnet |
사용 대상 | Public Subnet | Private Subnet |

---

## 사용 케이스

- Private EC2 의 패키지 다운로드
- 외부 API 호출
- 인터넷은 필요하지만 외부 노출은 금지

---

## 한 줄 정리

- NAT Gateway = "Private 에서 인터넷으로 요청은 가능하지만, 외부에서 직접 들어오는 것은 막는 구조"