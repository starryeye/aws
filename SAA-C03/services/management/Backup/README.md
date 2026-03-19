## AWS Backup

- AWS에서 제공하는 중앙 집중식 백업 관리 서비스
    - 여러 AWS 서비스의 백업을 통합 관리

---

- 특징
    - 완전 관리형
        - 백업 인프라 관리 불필요
    - 중앙 관리
        - 다양한 서비스 백업을 하나로 관리
    - 자동화
        - 백업 스케줄 및 정책 설정 가능
    - 보안
        - 암호화 및 접근 제어 지원

---

- 지원 서비스

    - EBS
    - RDS / Aurora
    - DynamoDB
    - EFS
    - FSx
    - EC2 (EBS 기반)

---

- 핵심 개념

    - Backup Plan
        - 백업 정책 정의 (스케줄, 보관 기간 등)

    - Backup Vault
        - 백업 데이터 저장소

    - Backup Rule
        - 백업 주기 및 조건 설정

    - Recovery Point
        - 백업된 특정 시점 데이터

---

- 동작 흐름

  Resource → Backup Plan → Backup 실행 → Backup Vault 저장

---

- 주요 기능

    - 자동 백업
        - cron / rate 기반 스케줄

    - 수명 주기 관리 (Lifecycle)
        - Warm → Cold storage 전환

    - Cross-Region Backup
        - 다른 리전에 백업 복사

    - Cross-Account Backup
        - 다른 계정으로 백업 복제

---

- 보안

    - KMS 기반 암호화
    - IAM 정책으로 접근 제어

---

## 사용 케이스

- 데이터 보호 (DR)
- 규정 준수 (compliance)
- 장기 보관

---

## 한 줄 정리

- AWS Backup = "여러 AWS 서비스의 백업을 중앙에서 관리하는 서비스"

---

- 참고

    - 서비스별 개별 백업 대신 통합 관리
    - 정책 기반 자동 백업 가능