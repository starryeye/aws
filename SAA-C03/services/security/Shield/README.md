## AWS Shield

- AWS 에서 제공하는 **DDoS(Distributed Denial of Service) 방어 서비스**

---

### 🛡️ Shield 종류

#### 1. Shield Standard (기본 제공, 무료)
- 모든 AWS 고객에게 자동 적용
- **L3/L4 공격 방어**
    - SYN Flood
    - UDP Flood
    - Reflection 공격 (DNS, NTP 등)
- 별도 설정 없이 기본 보호 제공

---

#### 2. Shield Advanced (유료)
- 더 강력한 DDoS 방어 및 가시성 제공
- **L3/L4 + 고급 L7 보호**
- 주요 기능:
    - 실시간 공격 탐지 및 완화
    - 공격 트래픽에 대한 상세 분석 (Visibility)
    - AWS DDoS Response Team (DRT) 지원
    - 비용 보호 (DDoS로 인한 스케일 비용 보상)
    - WAF와 연동한 L7 방어 강화

---

### ⚙️ 보호 대상 서비스 (시험 포인트)
- CloudFront
- Route 53
- Global Accelerator
- Application Load Balancer (ALB)
- Elastic IP (EC2)

---

### 🔍 방어 가능한 공격
#### L3/L4
- SYN Flood
- UDP Flood
- ICMP Flood
- Reflection / Amplification 공격

#### L7 (Advanced에서 일부 대응)
- HTTP Flood (WAF와 함께 사용 시 효과적)

---

### 🔗 WAF와의 관계 (중요)
- **Shield → 네트워크 레벨 보호 (L3/L4 중심)**
- **WAF → 애플리케이션 레벨 보호 (L7)**

👉 같이 사용하는 것이 베스트 프랙티스

---

### ⚠️ 한계
- Shield 단독으로는 **정교한 L7 공격 방어 한계**
- 애플리케이션 레벨 필터링은 WAF 필요

---

### 🧠 핵심 포인트
- Shield Standard = **기본 제공, 자동 L3/L4 보호**
- Shield Advanced = **유료 + 고급 보호 + 비용 보호**
- DDoS 문제 나오면:
    - L3/L4 → Shield
    - L7 → WAF
- **CloudFront + Shield + WAF 조합 = 정석 아키텍처**

---

### 💡 한 줄 정리
> AWS Shield는 DDoS 공격을 방어하는 서비스로,  
> 기본적으로 L3/L4 보호를 제공하며 WAF와 함께 L7까지 보완한다.