## Site-to-Site VPN

- 온프레미스 네트워크와 AWS VPC 를
  인터넷을 통해, 암호화하여 안전하게 연결하는 VPN(Virtual Private Network) 서비스

---

## 핵심 개념

- 회사 내부 네트워크 ↔ VPC 연결
- IPSec 터널을 사용한 암호화 통신

---

## 특징

    - 인터넷 기반 연결
    - 암호화 통신 (IPSec)
    - 빠르게 구축 가능
    - 비용 저렴
    - Direct Connect 대비 성능 낮음

---

## 구성 요소

### 1️⃣ Virtual Private Gateway (VGW)

- VPC 측 게이트웨이

---

### 2️⃣ Customer Gateway (CGW)

- 온프레미스 측 장비 (라우터 / 방화벽)

---

### 3️⃣ VPN Connection

- VGW ↔ CGW 연결

---

### 4️⃣ Tunnel (2개)

- 고가용성을 위해 2개의 터널 제공

---

## 동작 구조

    On-Premises
        ↓ (IPSec VPN)
    Customer Gateway (CGW)
        ↓
    Internet
        ↓
    Virtual Private Gateway (VGW)
        ↓
    VPC

---

## 특징 정리

- 인터넷을 통해 연결하지만 암호화됨
- 온프레미스와 AWS를 하나의 네트워크처럼 사용 가능
- BGP 지원 (동적 라우팅)

---

## 사용 케이스

- 온프레미스 → AWS 연결
- 하이브리드 클라우드 구성
- 빠른 마이그레이션

---

## Site-to-Site VPN vs Direct Connect

| 구분 | Site-to-Site VPN | Direct Connect |
|---|---|---|
경로 | 인터넷 | 전용 회선 |
보안 | 암호화 (IPSec) | 물리적 격리 |
성능 | 중간 | 매우 높음 |
구축 속도 | 빠름 | 느림 |
비용 | 저렴 | 비쌈 |

---

## 한 줄 정리

- Site-to-Site VPN = "온프레미스와 AWS 를 인터넷 기반 VPN 으로 연결"