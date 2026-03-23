## WAF (Web Application Firewall)

- AWS WAF는 웹 애플리케이션 앞단에서 HTTP/HTTPS 요청을 검사하여 공격 트래픽을 차단하는 서비스
- **L7 (Application Layer)** 에서 동작하며 요청의 **내용 기반 필터링** 수행
  - L7 기반 보안이지만, IP 를 베이스로 하여 설정한다.

---

### 🔍 검사 대상
- URI (Path, Query String)
- HTTP Header
- HTTP Body
- Cookie
- HTTP Method (GET, POST 등)
- Client IP (요청에서 추출하여 활용)

---

### 🛡️ 방어 가능한 공격 (L7)
- SQL Injection (SQLi)
- Cross-Site Scripting (XSS)
- HTTP Flood (L7 DDoS)
- 악성 봇 / 크롤링 / 스크래핑
- 비정상적인 요청 패턴

---

### ⚙️ 주요 기능
- **Rule 기반 필터링**
    - Allow / Block / Count
- **Managed Rule**
    - AWS 제공 룰셋 (OWASP Top 10 대응)
- **Rate-based Rule**
    - 특정 IP의 과도한 요청 차단
- **IP / Geo Match**
    - IP 또는 국가 기반 접근 제어
- **Bot Control**
    - 자동화 트래픽 탐지 및 차단
- **Logging & Monitoring**
    - CloudWatch, Kinesis 연동

---

### 🔗 연동 서비스 (시험 포인트)
- CloudFront (Edge에서 WAF 적용)
- Application Load Balancer (ALB)
- API Gateway
- AppSync

---

### ⚠️ 한계
- **L3/L4 공격 방어 불가**
    - SYN Flood, UDP Flood 등
- 네트워크 레벨 보호는 별도 서비스 필요
    - Security Group / NACL
    - AWS Shield (DDoS 방어)

---

### 🧠 핵심 포인트
- WAF = **L7 (HTTP/HTTPS) 보호**
- **CloudFront + WAF 조합 = 글로벌 엣지 보안**
- **Rate-based rule → DDoS 완화**
- **Managed Rule → 빠른 보안 적용**
- L4 공격은 **WAF가 아니라 Shield / SG 문제**

---

### 💡 한 줄 정리
> AWS WAF는 HTTP 요청 내용을 기반으로 공격을 차단하는 L7 보안 서비스이며,  
> 네트워크(L3/L4) 공격은 방어하지 않는다.