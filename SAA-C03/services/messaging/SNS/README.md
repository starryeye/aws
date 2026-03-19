## SNS (Simple Notification Service)

- AWS 에서 제공하는 메시지 발행/구독(Pub/Sub) 서비스
    - 하나의 메시지를 여러 구독자에게 전달

---

- 특징
    - Push 모델
        - 메시지를 구독자에게 자동 전달
    - Fan-out 구조
        - 하나의 메시지를 여러 소비자에게 전달
    - 완전 관리형
        - 서버 관리 불필요
    - 높은 확장성
        - 대량 메시지 처리 가능

---

- 동작 방식

  Publisher → SNS Topic → Subscriber (push)

---

- 주요 개념

    - Topic
        - 메시지 전달 채널

    - Publisher
        - 메시지를 보내는 주체

    - Subscriber
        - 메시지를 받는 대상

---

- Subscriber 유형

    - SQS
    - Lambda
    - HTTP / HTTPS Endpoint
    - Email / SMS

---

- 주요 기능

    - Message Filtering
        - 특정 조건에 맞는 메시지만 전달

    - Fan-out
        - SNS → 여러 SQS 큐 전달

    - Retry / Delivery Policy
        - 전송 실패 시 재시도

---

- 통합 서비스

    - SQS
        - 비동기 큐와 결합 (fan-out 패턴)

    - Lambda
        - 이벤트 기반 처리

    - EventBridge (간접적으로 활용)

---

## 사용 케이스

- 이벤트 브로드캐스트
- 알림 시스템 (SMS, Email)
- 마이크로서비스 이벤트 전달

---

## 한 줄 정리

- SNS = "하나의 메시지를 여러 구독자에게 전달하는 Pub/Sub 서비스"

---

- 참고

    - Push 방식
    - 여러 Consumer가 동일 메시지 수신 가능