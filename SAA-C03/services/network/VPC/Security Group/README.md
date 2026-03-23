## Security Group

- AWS 리소스(EC2, RDS 등)에 적용되는 가상 방화벽
    - 트래픽을 허용(Allow) 방식으로 제어
      - 허용할 IP 범위와 port 를 설정한다.
      - TCP/IP 기반 L4 보안

---

## 핵심 개념

- Instance 수준에서 동작하는 "허용 기반 방화벽"

---

## 특징

    - 기본적으로 Inbound 규칙은 모두 차단, Outbound 규칙은 모두 허용
    - Allow rule only (Deny 없음)
        - 특정 트래픽에 대해 접근 허용 설정은 가능하지만, 접근 차단 설정은 불가능(black list 불가)
    - 하나의 SG 에 여러 개의 AWS 리소스를 포함할 수 있다.
    - 특정 서브넷에 종속되지 않고 여러 AWS 리소스를 하나의 SG 로 묶을 수 있다.

---

## 동작 방식

---

### 1️⃣ Inbound (들어오는 트래픽)

- 기본: 모두 차단
- 명시적으로 허용해야 접근 가능

예:

    TCP 80 → 0.0.0.0/0 허용

→ 웹 서버 접근 가능

---

### 2️⃣ Outbound (나가는 트래픽)

- 기본: 모두 허용
- 필요 시 제한 가능

---

## Stateful (가장 중요)

- 요청이 허용되면 응답은 자동 허용됨

---

### 예시

    Inbound: TCP 80 허용

→ Client → EC2 요청 ⭕  
→ EC2 → Client 응답 ⭕ (자동 허용)

👉 Outbound 규칙 없어도 됨

---

## 규칙 구성 요소

- Protocol (TCP / UDP / ICMP)
- Port Range (예: 80, 443)
- Source / Destination
    - IP (0.0.0.0/0)
    - CIDR
    - Security Group

---

## Security Group 참조 (중요)

👉 SG를 Source로 지정 가능

예:

    SG-B → SG-A 접근 허용

→ 특정 서버 그룹끼리만 통신

---

## 특징 정리

- 서버 단위 보안
- 상태 기반 (Stateful)
- 허용 규칙만 존재

---

## 사용 케이스

- 웹 서버 (80, 443 허용)
- DB 서버 (특정 SG만 허용)
- 내부 서비스 통신

---

## Security Group vs NACL

| 구분 | Security Group | NACL |
|---|---|---|
적용 대상 | Instance | Subnet |
상태 | Stateful | Stateless |
규칙 | Allow only | Allow + Deny |
응답 처리 | 자동 허용 | 별도 설정 필요 |

---

## 한 줄 정리

- Security Group = "EC2에 붙는 상태 기반 허용형 방화벽"