## NACL (Network Access Control List)

- Subnet 단위에서 동작하는 가상 방화벽
    - 네트워크 레벨에서 트래픽 제어
    - TCP/IP 기반 L4 보안

---

## 핵심 개념

- Subnet 수준에서 트래픽을 제어하는 방화벽
- Allow + Deny 규칙 모두 가능

---

## 특징

    - Allow + Deny 규칙 모두 존재
    - Subnet 단위 적용
    - 기본적으로 모든 트래픽 허용 (default NACL 기준)
    - 오직 IP 만 활용하여 규칙 설정 가능 (AWS 리소스 활용하여 규칙 설정 불가)

---

## 동작 방식

---

### 1️⃣ Inbound

- 규칙 순서대로 평가
- 허용 또는 차단

---

### 2️⃣ Outbound

- Inbound와 별도로 규칙 설정 필요

---