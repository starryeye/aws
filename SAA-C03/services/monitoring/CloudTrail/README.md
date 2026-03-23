## AWS CloudTrail

- AWS 계정에서 발생하는 **API 호출 및 사용자 활동을 기록하는 서비스**
- “누가, 언제, 무엇을 했는지”를 추적 (감사/보안 핵심 서비스)

---

### 🔍 기록 대상

- AWS Management Console 사용
- AWS CLI / SDK 호출
- 서비스 간 API 호출
- IAM 활동 (권한 변경 등)

👉 모든 것은 결국 **API 호출 이벤트로 기록됨**

---

### 📦 이벤트 종류

#### 1. Management Events (기본)
- 리소스 관리 작업
- 예:
    - EC2 생성/삭제
    - IAM 정책 변경

---

#### 2. Data Events (옵션, 비용 추가)
- 리소스 내부 데이터 접근
- 예:
    - S3 객체 조회 (GetObject)
    - Lambda 함수 실행

---

#### 3. Insights Events
- 비정상적인 API 호출 패턴 탐지
- 예:
    - 갑작스러운 호출 증가
    - 이상 행동

---

### ⚙️ 주요 기능

- API 호출 이력 기록 (감사 로그)
- 보안 및 컴플라이언스 지원
- 이벤트 검색 및 분석
- 장기 저장 (S3 연동)

---

### 📂 저장 위치

- 기본:
    - Event History (최근 90일 조회 가능)
- 설정 시:
    - S3 버킷에 로그 저장 (장기 보관)
    - CloudWatch Logs 연동 가능

---

### 🔗 연동 서비스

- S3 (로그 저장)
- CloudWatch Logs (실시간 분석)
- EventBridge (이벤트 기반 자동 대응)
- GuardDuty (위협 탐지 데이터 활용)

---

### 🛡️ 활용 사례

- 누가 IAM 정책을 변경했는지 확인
- 특정 리소스 삭제 원인 추적
- 보안 사고 분석 (Forensics)
- 규정 준수 감사 (Compliance)

---

### ⚠️ 특징

- 기본적으로 **모든 AWS 계정에 활성화됨**
- Data Events는 별도 설정 필요 (유료)
- 실제 리소스 상태가 아니라 **API 호출 기록**임

---

### 🧠 핵심 포인트

- CloudTrail = **API 호출 로그 서비스**
- “누가, 언제, 무엇을 했는지” 추적
- 기본 90일 Event History 제공
- S3 저장으로 장기 보관
- Data Events는 추가 비용
- GuardDuty는 CloudTrail 로그를 활용

---

### ⚖️ 서비스 비교

| 서비스 | 역할 |
|--------|------|
| CloudTrail | API 호출 로그 |
| CloudWatch | 메트릭/로그 모니터링 |
| GuardDuty | 위협 탐지 |
| Macie | 데이터 보안 |

---

### 💡 한 줄 정리
> AWS CloudTrail은 AWS 계정에서 발생한 API 호출을 기록하여  
> 보안 감사와 추적을 가능하게 하는 서비스이다.