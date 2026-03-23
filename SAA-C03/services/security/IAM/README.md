## AWS IAM (Identity and Access Management)

- AWS 리소스에 대한 **인증(Authentication) + 인가(Authorization)**를 관리하는 서비스
- **누가(Who) 어떤 리소스에 무엇을 할 수 있는지(What)**를 정의

---

### 🔑 핵심 개념

#### 1. User (사용자)
- AWS 에 로그인하는 개별 사용자
- 사람 또는 애플리케이션 계정
- IAM 사용자는 AWS 서비스에 접근할 수 있는 Access Key 를 발급받아 사용한다.
  - Access Key 는 만료 없음, 발급 후 회수 불가능
    - 유출되면 치명적이라 IAM Role 을 사용하는것을 권장

#### 2. Group (그룹)
- 여러 User를 묶어서 권한 관리
- User는 여러 Group에 속할 수 있음

#### 3. Role (역할)
- 특정 권한(Policy)을 가진 IAM 엔티티
- 사용자(User) 또는 서비스(EC2, Lambda 등)가 **AssumeRole을 통해 임시 자격 증명을 발급받아 사용**
- Access Key 같은 장기 자격 증명을 직접 공유할 필요 없음
  - STS를 통해 **임시 자격 증명** 사용
- 필요 시 권한 회수(Policy 변경 또는 Role 제거) 가능

- 예:
  - EC2 → Role을 Assume하여 S3 접근
  - 다른 계정의 Role을 Assume하여 Cross Account 접근

#### 4. Policy (정책)
- 권한을 정의하는 JSON 문서
- "Allow / Deny" 기반

---

### 📜 Policy 구조

```json
{
  "Effect": "Allow",
  "Action": "s3:GetObject",
  "Resource": "arn:aws:s3:::my-bucket/*"
}