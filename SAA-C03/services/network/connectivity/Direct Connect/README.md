## Direct Connect

- 온프레미스와 AWS를
  인터넷을 거치지 않고 전용 회선으로 연결하는 서비스

---

## 핵심 개념

- 회사 네트워크 ↔ AWS 전용 네트워크 연결
- Public Internet 을 사용하지 않음

---

## 특징

    - 전용 회선 (Dedicated network)
    - 인터넷 경유 ❌
    - 높은 대역폭 / 낮은 지연
    - 안정적인 네트워크 품질
    - 보안성 높음 (물리적 격리)

---

## 구성 요소

### 1️⃣ Direct Connect Location

- AWS와 연결되는 물리적 데이터 센터

---

### 2️⃣ Connection

- 온프레미스 ↔ AWS 물리적 연결

---

### 3️⃣ Virtual Interface (VIF)

- 논리적 연결

    - Private VIF → VPC 연결
    - Public VIF → AWS Public 서비스(S3 등)

---

## 동작 구조

    On-Premises
        ↓
    Direct Connect (전용 회선)
        ↓
    AWS Network
        ↓
    VPC / AWS 서비스

---

## 특징 정리

- 인터넷을 사용하지 않음
- 매우 안정적인 네트워크
- 고성능 데이터 전송 가능
- 구축 시간 오래 걸림

---

## 사용 케이스

- 대용량 데이터 전송
- 금융 / 기업 시스템
- 안정적인 하이브리드 환경

---

## Direct Connect vs Site-to-Site VPN

| 구분 | Direct Connect | Site-to-Site VPN |
|---|---|---|
경로 | 전용 회선 | 인터넷 |
보안 | 물리적 격리 | 암호화 (IPSec) |
성능 | 매우 높음 | 중간 |
지연 | 낮음 | 상대적으로 높음 |
구축 | 느림 | 빠름 |
비용 | 비쌈 | 저렴 |

---

## 한 줄 정리

- Direct Connect = "온프레미스와 AWS 를 전용 회선으로 연결하는 고성능 네트워크"