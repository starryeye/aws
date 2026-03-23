## AWS IAM Identity Center (구 AWS SSO)

- AWS 계정 및 애플리케이션에 대한 **통합 인증(SSO) 및 접근 중앙 관리 서비스**
- 여러 AWS 계정과 외부 애플리케이션에 **하나의 계정으로 로그인 (Single Sign-On)** 제공

---

### 🔑 핵심 개념

- SSO AuthN 처리
- AuthZ 처리
  - 사용자 또는 그룹 단위로 Permission Set(권한 set) 부여 가능
- 외부 IdP 연동가능
  - Google Workspace, Okta, Auth0, 온프레미스AD 등
- MFA 설정 강제 가능
  - OTP, SMS 인증 등

---

### 👥 주요 구성 요소

#### 1. User / Group
- Identity Center에서 관리되는 사용자 및 그룹

#### 2. Permission Set
- IAM Role + Policy를 추상화한 개념
- 특정 AWS 계정에 대한 권한 정의

#### 3. AWS Account 할당
- 사용자/그룹 + Permission Set을 특정 계정에 매핑

👉 결과:
- 사용자는 로그인 후 여러 계정에 쉽게 접근 가능

---

### ⚙️ 동작 방식

1. 사용자가 Identity Center 에 로그인
2. 접근 가능한 AWS 계정 목록 확인
3. 계정 선택
4. 해당 계정의 IAM Role 을 Assume 하여 접근

---

### 🔗 연동 대상

- AWS Organizations (멀티 계정 환경)
- 외부 Identity Provider (SAML 2.0 기반)
- SaaS 애플리케이션 (예: Salesforce, Google Workspace 등)

---

### 🔐 주요 기능

- 중앙 집중식 사용자 및 권한 관리
- AWS 계정 간 접근 통합 관리
- SAML 기반 외부 IdP 연동
- MFA 지원
- 임시 자격 증명 (Role 기반 접근)

---

### ⚠️ IAM과의 차이

| 구분 | IAM | IAM Identity Center |
|------|-----|---------------------|
| 대상 | 단일 계정 중심 | 멀티 계정 / 조직 |
| 사용자 관리 | 계정 단위 | 중앙 집중 관리 |
| 로그인 방식 | 개별 계정 로그인 | SSO |
| 권한 방식 | Policy 직접 관리 | Permission Set |

---

### 🧠 핵심 포인트

- Identity Center = **SSO + 중앙 계정 관리**
- AWS Organizations와 함께 사용
- Permission Set → IAM Role로 매핑됨
- 외부 IdP 연동 가능 (SAML)
- 멀티 계정 환경에서 권장 방식
- MFA 설정 강제

---

### 💡 한 줄 정리
> AWS IAM Identity Center는 여러 AWS 계정과 애플리케이션에 대해  
> SSO 기반으로 중앙 집중식 인증과 권한 관리를 제공하는 서비스이다.