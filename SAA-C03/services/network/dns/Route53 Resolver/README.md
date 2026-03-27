## Route53 Resolver

- VPC 내부에서 DNS 요청을 처리하는 서비스
  - 기본적으로 VPC의 DNS 서버 역할

---

## 핵심 개념

- 원래는 IP 기반 통신
- Resolver를 통해 "도메인 기반 통신" 가능

---

## As-Is → To-Be

### ❌ As-Is (DNS 없을 때)

    EC2 → 10.0.1.23 (IP 직접 호출)

- IP를 직접 알아야 함
- IP 변경 시 문제 발생
- 확장/유지보수 어려움

---

### ✅ To-Be (Resolver 사용)

    EC2 → db.internal.local (도메인)
          ↓
       Resolver
          ↓
    10.0.1.23 (IP)

- 도메인 기반 통신
- IP 변경 영향 없음
- 서비스 추상화 가능

---

## 기본 역할 (Core)

- VPC 내부 DNS 서버

  EC2 → Resolver → 도메인 → IP 반환

---

## 특징

    - VPC마다 기본 제공됨
    - 별도 생성 필요 없음
    - AWS 내부 DNS 처리

---

## 기본 DNS 주소

    VPC CIDR + 2

예:
10.0.0.0/16 → 10.0.0.2

---

## 주요 기능 (As-Is → To-Be 관점)

---

### 1️⃣ AWS 내부 DNS 해석

#### ❌ As-Is

    EC2 → S3 IP 직접 사용

#### ✅ To-Be

    EC2 → s3.amazonaws.com → Resolver → IP

👉 AWS 서비스도 도메인 기반 접근

---

### 2️⃣ VPC 내부 이름 해석

#### ❌ As-Is

    EC2 → 다른 EC2 IP 직접 접근

#### ✅ To-Be

    EC2 → app.internal → Resolver → IP

👉 내부 서비스 간 도메인 기반 통신

---

## 확장 기능 (Hybrid DNS)

👉 Resolver + Endpoint = 온프레 연동

---

### 3️⃣ Outbound Endpoint

- AWS 서비스가 On-Prem 내부에서만 사용하는 도메인 주소를 해석해주는 기능으로..
  - AWS 서비스가 On-Prem 내부에서만 사용하는 도메인 주소로 요청 보낼 수 있게됨.

#### ❌ As-Is

    EC2 → On-Prem 서버 (IP로만 접근)

#### ✅ To-Be

    EC2 → db.corp.local
          ↓
       Resolver
          ↓
    On-Prem DNS → IP 반환

👉 AWS → 온프레 도메인 통신 가능

---

### 4️⃣ Inbound Endpoint

#### ❌ As-Is

    On-Prem → AWS (IP 기반 접근)

#### ✅ To-Be

    On-Prem → app.aws.local
             ↓
          Resolver
             ↓
          EC2

👉 온프레 → AWS 도메인 기반 접근

---

### 5️⃣ Resolver Rules

#### ❌ As-Is

    모든 DNS 요청 동일 처리

#### ✅ To-Be

    *.corp.local → On-Prem DNS
    *.aws.local → AWS Resolver

👉 도메인별 라우팅 가능

---

## 핵심 구조

### 기본

    EC2 → Resolver → AWS DNS

---

### Hybrid

    On-Prem ↔ Resolver ↔ VPC

---

## 핵심 이해

- Resolver = DNS 서버
- Endpoint = 외부 DNS 연결

---

## Route53 vs Resolver

| 구분 | Route53 | Route53 Resolver |
|---|---|---|
역할 | Public DNS | 내부 DNS |
대상 | 외부 사용자 | EC2 / 내부 시스템 |
기능 | 도메인 연결 | DNS 해석 + 연동 |

---

## 특징 정리

- IP → 도메인 기반 통신으로 추상화
- 내부 DNS 처리
- 온프레 DNS까지 확장 가능

---

## 한 줄 정리

- Route53 Resolver = "IP 기반 통신을 도메인 기반으로 추상화하고, 온프레까지 연결하는 내부 DNS"