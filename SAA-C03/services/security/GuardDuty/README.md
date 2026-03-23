## Amazon GuardDuty

- AWS에서 제공하는 **지능형 위협 탐지 서비스 (Threat Detection Service)**
-  **계정/워크로드에서 발생하는 이상 행위 탐지**

---

### 🔍 데이터 소스 (시험 핵심)
GuardDuty는 아래 로그를 분석하여 위협을 탐지:

- **VPC Flow Logs**
    - 네트워크 트래픽 이상 탐지
- **AWS CloudTrail**
    - API 호출 이상 행위 탐지
- **DNS Logs**
    - 악성 도메인 통신 탐지
- (옵션)
    - EKS Audit Logs
    - S3 Data Events

---

### 🛡️ 탐지 가능한 위협 유형
- 비정상적인 API 호출 (예: 루트 계정 사용, 권한 상승 시도)
- 크리덴셜 탈취 의심 활동
- 포트 스캔 / 네트워크 스캐닝
- 백도어 / C2 서버 통신
- 암호화폐 채굴 (Crypto Mining)
- 악성 IP / 도메인과 통신

---

### ⚙️ 주요 특징
- **완전 관리형 서비스**
    - 별도 인프라 구성 필요 없음
- **자동 활성화 가능 (원클릭)**
- **머신러닝 기반 이상 탐지**
- **Threat Intelligence 연계**
    - AWS + 외부 보안 데이터 활용
- **Finding 생성**
    - 위협 발견 시 이벤트로 제공

---

### 📊 결과 처리 (중요)
- 탐지 결과는 **Finding** 형태로 제공
- 연동 가능:
    - EventBridge → 자동 대응
    - Lambda → 대응 로직 실행
    - Security Hub → 통합 보안 관리

---

### 🔗 연관 서비스
- Security Hub (보안 통합 대시보드)
- IAM (권한 이상 탐지)
- CloudTrail (로그 소스)
- VPC (네트워크 로그)

---

### ⚠️ 역할 범위 (중요 구분)
- GuardDuty = **탐지 (Detect)**
- 차단 / 대응은 직접 수행하지 않음

👉 대응은 별도 서비스 필요:
- Lambda
- WAF
- Security Group 수정 등

---

### 🧠 핵심 포인트
- GuardDuty = **계정 관련 위협 탐지 서비스 (Detection)**
- 로그 기반 분석:
    - VPC Flow Logs + CloudTrail + DNS Logs
- 머신러닝 + 위협 인텔리전스 사용
- **자동 대응 X → Finding 제공**
- 대응 자동화는 EventBridge + Lambda

---

### ⚖️ 서비스 비교

| 서비스 | 역할 |
|--------|------|
| WAF | L7 공격 차단 |
| Shield | DDoS 방어 (L3/L4) |
| GuardDuty | 위협 탐지 (로그 분석) |

---

### 💡 한 줄 정리
> Amazon GuardDuty는 AWS 환경의 로그를 분석하여  
> 계정관련 이상 행위와 보안 위협을 탐지하는 서비스이다.