## Route53

- AWS에서 제공하는 DNS (Domain Name System) 서비스
    - 도메인 이름을 IP 주소로 변환

---

## 핵심 개념

- 사용자가 입력한 도메인 → 실제 서버(IP)로 연결
- "어디로 보낼지 결정"하는 서비스

---

## 역할

    www.example.com → 1.2.3.4

---

## 특징

    - 글로벌 서비스
    - 고가용성 (Highly Available)
    - 확장성
    - 다양한 라우팅 정책 지원

---

## 구성 요소

### 1️⃣ Hosted Zone

- 도메인 관리 공간

---

### 2️⃣ Record

- 도메인과 대상 리소스 매핑

    - A → IP 주소
    - CNAME → 다른 도메인
    - Alias → AWS 리소스 (ALB, CloudFront 등)

---

## Routing Policy (핵심)

- DNS 요청을 어떻게 분배할지 결정하는 정책

---

### 1️⃣ Simple Routing (단순 라우팅)

- 단일 리소스로 연결
- 기본 DNS 동작

---

### 2️⃣ Weighted Routing (가중치 기반 라우팅)

- 트래픽을 미리 설정한 비율로 분배

  예:
    - 90% → v1
    - 10% → v2

- A/B 테스트, Blue/Green 배포

---

### 3️⃣ Latency-Based Routing (지연시간 기반 라우팅)

- 가장 낮은 latency를 가진 리전으로 연결

- 글로벌 서비스

---

### 4️⃣ Failover Routing (장애 극복 라우팅)

- Primary 장애 시 Secondary로 전환

- Health Check 필요
- DR (재해 복구)

---

### 5️⃣ Geolocation Routing (지리적 위치 라우팅)

- 사용자 "위치(국가/대륙)" 기준 라우팅

---

### 6️⃣ Geoproximity Routing (지리적 근접 라우팅)

- 사용자와 리소스 "거리" 기준 라우팅
- bias 설정으로 트래픽 조정 가능

---

### 7️⃣ Multi-Value Answer Routing (다중값 응답 라우팅)

- 여러 IP 반환 (최대 8개) 하여 트래픽을 분산하는 효과
- Health Check 기반으로 정상 서버만 응답

---

### 8️⃣ IP-Based Routing (IP 기반 라우팅)

- 클라이언트의 IP 주소 범위(CIDR) 기준 라우팅
  - 클라이언트의 IP 에 따라 특정 리소스로 라우팅한다.

- 특정 고객 / 내부망 / 보안 정책

---

## Routing Policy 비교

| 정책 | 기준 | 특징 | 사용 케이스 |
|---|---|---|---|
Simple | 없음 | 기본 DNS | 단일 서버 |
Weighted | 비율 | 트래픽 분산 | A/B 테스트 |
Latency | 속도 | 가장 빠른 리전 | 글로벌 서비스 |
Failover | 상태 | 장애 시 전환 | DR |
Geolocation | 위치 | 국가 기준 | 지역 서비스 |
Geoproximity | 거리 | 거리 + bias | 트래픽 조정 |
Multi-value | Health | 여러 IP 반환 | 간단 LB |
IP-based | IP | IP 기준 | 보안 / 내부망 |

