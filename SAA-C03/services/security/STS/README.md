## AWS STS (Security Token Service)

- AWS에서 제공하는 **임시 자격 증명(Temporary Credentials) 발급 서비스**
- 일정 시간 동안만 유효한 **Access Key / Secret Key / Session Token** 생성

---

### 🔑 핵심 개념

- 영구 자격 증명 대신 **짧은 수명의 임시 자격 증명 사용**
- 보안성 향상 (유출 시 피해 최소화)
- 주로 **Role 기반 접근**에서 사용됨

---

### 📦 제공되는 자격 증명

- Access Key ID
- Secret Access Key
- Session Token
- 유효 시간 (TTL, 기본 최대 몇 시간)

---

### ⚙️ 주요 기능

#### 1. AssumeRole
- 특정 Role을 임시 발급

👉 사용 예:
- EC2 → S3 접근
- 계정 A → 계정 B 접근 (Cross Account)

---

#### 2. AssumeRoleWithSAML
- SAML 기반 외부 IdP 사용자 인증
- 기업 SSO 환경에서 사용

---

#### 3. AssumeRoleWithWebIdentity
- OAuth/OpenID 기반 인증
- 모바일 앱 / 웹 앱에서 사용

---

#### 4. GetSessionToken
- IAM User가 MFA 인증 후 임시 자격 발급

---

### 🔗 사용 시나리오

#### 1. EC2에서 AWS 서비스 접근
- EC2에 Role 부여 → 내부적으로 STS 사용
- Access Key 저장 불필요 (보안 Best Practice)

---

#### 2. Cross Account Access
- 다른 AWS 계정의 리소스 접근
- Role Assume + STS 토큰 사용

---

#### 3. SSO / Identity Center
- 로그인 후 Role Assume 시 STS 사용

---

#### 4. 임시 사용자 권한 부여
- 외부 사용자에게 제한된 시간 동안 접근 허용

---

### 🔐 보안 특징

- **짧은 수명 (Temporary)**
- 자동 만료
- 재발급 필요
- Access Key를 장기 저장하지 않아도 됨

---

### ⚠️ IAM과 관계

- IAM → “권한 정의”
- STS → “그 권한을 임시로 발급”

👉 즉:
> IAM Role + STS = 실제 인증/인가 동작

---

### 🧠 핵심 포인트

- STS = **임시 자격 증명 발급 서비스**
- AssumeRole = 핵심 기능
- Cross Account 접근 = STS 사용
- EC2 Role 사용 시 내부적으로 STS 동작
- Access Key를 코드에 저장하지 않는 이유 → STS 사용

---

### ⚖️ 서비스 비교

| 서비스 | 역할 |
|--------|------|
| IAM | 권한 정의 |
| STS | 임시 자격 발급 |
| Identity Center | SSO / 중앙 인증 |
| WAF | L7 공격 차단 |

---

### 💡 한 줄 정리
> AWS STS는 IAM Role을 기반으로  
> 일정 시간 동안만 유효한 임시 자격 증명을 발급하는 서비스이다.