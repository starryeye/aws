## SQS (Simple Queue Service)

- AWS 에서 제공하는 메시지 큐 서비스
    - 서비스 간 비동기 통신을 위한 메시지 저장소

---

- 특징
    - 완전 관리형
        - 서버 관리 불필요
    - 비동기 처리
        - 시스템 간 결합도 감소 (decoupling)
    - 높은 확장성
        - 대량 메시지 처리 가능
    - 내구성
        - 메시지 다중 AZ 저장
    - Pull 모델 큐
    - 갑자기 몰리는 트래픽에도 메시지를 큐에 쌓아 둠으로 메시지 손실 없이 처리 가능
    - 하나의 메시지는 하나의 컨슈머만 처리가능하다.
        - 여러 컨슈머가 있다면 경쟁 소비된다.

---

- 동작 방식

  Producer → SQS → Consumer (polling)

---

- 메시지 처리

    - 메시지 저장 → Consumer가 가져감 (pull)
    - 처리 후 → 삭제(delete)

---

- 주요 개념

    - Message
        - 전달되는 데이터

    - Queue
        - 메시지 저장 공간

    - Visibility Timeout
        - 메시지를 가져간 후 일정 시간 동안 다른 Consumer에게 숨김

    - Long Polling
        - 메시지 도착까지 대기 (불필요한 요청 감소)

---

- Queue 유형

    - Standard Queue
        - at-least-once delivery (중복 가능)
        - 순서 보장 ❌
        - 높은 처리량

    - FIFO Queue
        - exactly-once processing (중복 없음)
        - 순서 보장 ⭕
        - 처리량 제한

---

- 주요 기능

    - Dead Letter Queue (DLQ)
        - 처리 실패 메시지 별도 보관

    - Delay Queue
        - 메시지 지연 전송

    - Message Retention
        - 메시지 보관 기간 설정 (최대 14일)

---

- 통합 서비스

    - Lambda
        - SQS 이벤트 기반 처리

    - SNS
        - Fan-out 구조 (SNS → 여러 SQS)

    - EC2 / ECS
        - Worker 기반 처리

---

## 사용 케이스

- 비동기 작업 처리
- 트래픽 버퍼링
- 마이크로서비스 간 메시지 전달

---

## 한 줄 정리

- SQS = "비동기 처리를 위한 메시지 큐"

---

- 참고

    - Pull 방식 (Consumer가 가져감)
    - 하나의 메시지는 하나의 Consumer가 처리