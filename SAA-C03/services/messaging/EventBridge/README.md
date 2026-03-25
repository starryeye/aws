## EventBridge

- AWS에서 제공하는 이벤트 버스(Event Bus) 서비스
    - 다양한 소스(AWS 서비스)에서 발생한 AWS 자체 이벤트를 기반으로 서비스 간 연결

---

- 특징
    - 이벤트 기반 아키텍처 지원 (Event-driven)
      - AWS 자체 이벤트, cron/rate(스케쥴) 기반 이벤트 생성기반
    - 완전 관리형
    - 다양한 AWS 서비스와 통합
    - 필터링 기반 라우팅

---

- 동작 방식

  Event Source → EventBridge → Rule → Target

---

- 주요 개념

    - Event Bus
        - 이벤트가 들어오는 통로

    - Event
        - 상태 변화 정보 (JSON 형태)

    - Rule
        - 이벤트 필터링 및 라우팅 조건

    - Target
        - 이벤트를 전달할 대상 (Lambda, SQS 등)

---

- Event Source

    - AWS 서비스 (EC2, S3, RDS 등)
    - Custom Application
    - SaaS 서비스

---

- Target

    - Lambda
    - SQS
    - SNS
    - Step Functions
    - ECS

---

- 주요 기능

    - Event Filtering
        - 특정 이벤트만 선택

    - Fan-out
        - 하나의 이벤트를 여러 Target으로 전달

    - Schedule
        - cron / rate 기반 실행 (CloudWatch Events 대체)

    - Schema Registry
        - 이벤트 구조 관리

---

- Event 유형

    - AWS 서비스 이벤트
    - Custom 이벤트
    - Scheduled 이벤트

---

## 사용 케이스

- 이벤트 기반 마이크로서비스
- AWS 서비스 이벤트 처리
  - S3 에 이미지 파일이 업로드 완료되면, Lambda 로 이미지 resizing 을 처리하고 싶을때..
  - S3 -> EventBride -> Lambda
- 스케줄 작업 (cron)
- SaaS 이벤트 통합

---

## 한 줄 정리

- EventBridge = "이벤트를 필터링하여 원하는 서비스로 라우팅하는 이벤트 버스"
