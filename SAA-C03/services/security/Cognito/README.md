## Amazon Cognito

- AWS에서 제공하는 **JWT 기반 사용자 인증/인가 서비스**

---

### 🔑 핵심 기능

#### 1. 사용자 인증 (Authentication)
- 회원가입 / 로그인 기능 제공
- 로그인 방식:
    - ID / Password
    - 소셜 로그인 (Google, Facebook, Apple 등)
    - SAML 기반 기업 인증

---

#### 2. 사용자 관리 (User Management)
- 사용자 디렉토리 제공
- 프로필 관리 (이메일, 전화번호 등)
- 비밀번호 정책 및 MFA 설정

---

#### 3. 토큰 기반 인증
- 로그인 성공 시 토큰 발급:
    - ID Token (사용자 정보)
    - Access Token (API 접근 권한)
    - Refresh Token (재발급용)

👉 JWT 기반 인증

---

### 🧩 주요 구성 요소

#### 1. User Pool
- 사용자 인증 및 관리
- 회원가입 / 로그인 처리
- JWT 토큰 발급

👉 “인증(Authentication)” 담당

---

#### 2. Identity Pool (Federated Identities)
- 인증된 사용자에게 AWS 리소스 접근 권한 부여
- IAM Role과 연동

👉 “인가(Authorization)” 담당

---

### ⚙️ 동작 흐름

```text id="d9c2xz"
1. 사용자 로그인 (User Pool)
2. JWT 토큰 발급
3. Identity Pool로 전달
4. IAM Role 매핑
5. STS를 통해 임시 자격 발급
6. AWS 리소스 접근 (S3 등)