## Step Functions

- AWS에서 제공하는 서버리스 워크플로우(오케스트레이션) 서비스
    - 여러 AWS 서비스를 순서/조건에 따라 연결하여 실행

---

- 특징
    - 서버리스
        - 인프라 관리 불필요
    - 상태 관리 (Stateful)
        - 실행 흐름과 상태를 유지
    - 시각화
        - 워크플로우를 그래프로 확인 가능
    - 내장 기능
        - retry / error handling / timeout 지원
    - 15분 이상의 장기 작업 가능

---

- 핵심 개념

    - State Machine
        - 전체 워크플로우 정의

    - State
        - 각 단계 (작업 단위)

---

- State 유형

    - Task
        - Lambda, ECS, SNS 등 실행

    - Choice
        - 조건 분기 (if/else)

    - Parallel
        - 병렬 처리

    - Wait
        - 일정 시간 대기

    - Pass
        - 데이터 전달

    - Fail / Succeed
        - 종료 상태

---

- 동작 흐름

  Event → State Machine → 여러 Step 실행 → 결과

---

- 실행 방식

    - Standard
        - 장기 실행 (최대 1년)
        - 정확한 실행 보장
        - 비용: 상태 전이 횟수 기준

    - Express
        - 짧고 빠른 실행
        - 고속 처리 (초당 수천 건)
        - 비용: 실행 횟수 + 시간 기준

---

- 주요 기능

    - Retry
        - 실패 시 자동 재시도

    - Error Handling
        - 예외 처리 흐름 정의

    - Timeout
        - 실행 시간 제한

---

- 통합 서비스

    - Lambda
    - ECS / Fargate
    - SQS / SNS
    - DynamoDB
    - API Gateway

---

## 사용 케이스

- 주문 처리 워크플로우
- ETL 파이프라인
- 데이터 처리 흐름
- 복잡한 비즈니스 로직 orchestration

---

## 한 줄 정리

- Step Functions = "여러 작업을 순서/조건/병렬로 실행하는 서버리스 워크플로우 엔진"

---

- 참고

    - 단일 작업 → Lambda
    - 복잡한 흐름 → Step Functions