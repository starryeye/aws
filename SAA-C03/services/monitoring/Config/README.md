## AWS Config

- AWS 리소스의 **구성(Configuration) 상태를 기록하고 변경 이력을 추적하는 서비스**
  - 리소스의 설정이 언제, 누가, 어떻게 변경되었는지

---

### 🔍 핵심 기능

#### 1. 리소스 구성 기록 (Configuration Recording)
- AWS 리소스의 설정 상태를 지속적으로 기록
- 예:
    - S3 버킷 공개 여부
    - 보안 그룹 인바운드 규칙
    - EC2 인스턴스 설정

---

#### 2. 변경 이력 추적 (Configuration History)
- 리소스 설정 변경 내역 저장
- “언제, 무엇이, 어떻게 변경되었는지” 확인 가능

---

#### 3. Config Rule (규정 준수 검사)
- 리소스가 특정 규칙을 준수하는지 평가

👉 예:
- S3 버킷은 반드시 암호화되어야 함
- 보안 그룹은 0.0.0.0/0 허용 금지

---

#### 4. 자동 평가 (Compliance Monitoring)
- 리소스 상태를 지속적으로 평가하여
    - COMPLIANT / NON_COMPLIANT 결과 제공

---

### 📊 결과 (Compliance)

- 리소스별 준수 여부 표시
- 위반 시 알림 및 자동 대응 가능

---

### 🔗 연동 서비스

- S3 (구성 기록 저장)
- CloudWatch / EventBridge (이벤트 기반 대응)
- Lambda (자동 수정)
- Security Hub (보안 통합)

---

### ⚙️ 동작 흐름

```text id="8ph9sn"
1. 리소스 생성/변경 발생
2. AWS Config가 구성 상태 기록
3. Config Rule로 평가 수행
4. Compliance 결과 생성
5. 필요 시 EventBridge → Lambda 자동 수정