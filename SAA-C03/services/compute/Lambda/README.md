## Lambda

- AWS 에서 제공하는 서버리스 컴퓨팅 서비스
    - 서버 없이 코드를 실행

---

- 특징
    - 서버리스 (Serverless)
        - 서버 프로비저닝 및 관리 불필요
    - 이벤트 기반 (Event-driven)
        - 이벤트 발생 시 자동 실행
    - 자동 확장
        - 요청 수에 따라 자동으로 scale out
    - 사용한 만큼 과금
        - 실행 시간(ms) + 요청 수 기반
    - Cold Start
        - 개념
            - 처음 실행 시 지연 발생
        - 해결
            - Provisioned Concurrency
                - warm 상태 유지
    - 최대 15분간 실행 시간을 보장한다.
        - 15분이 넘어가면 Lambda 에서 실행 불가

---

- 실행 방식

    - 이벤트 트리거 기반 실행
        - S3
        - API Gateway
        - SQS / SNS
        - DynamoDB Streams
        - EventBridge

---

- 구성 요소

    - Function
        - 실행 코드

    - Trigger
        - 실행 조건 (이벤트)

    - Execution Role
        - AWS 서비스 접근 권한

---

- 실행 환경

    - Runtime
        - Java, Node.js, Python, Go 등

    - Timeout
        - 최대 15분

    - Memory
        - 메모리 설정에 따라 CPU 성능 증가

---

- 동작 흐름

  Event 발생 → Lambda 실행 → 결과 반환

---

- 주요 기능

    - Concurrency
        - 동시에 실행 가능한 함수 수

    - Reserved Concurrency
        - 특정 함수에 리소스 보장

    - Provisioned Concurrency
        - cold start 제거

---

- 배포

    - Version / Alias
        - 버전 관리 및 트래픽 분산

---

- 통합 서비스

    - API Gateway
        - REST API 구성

    - S3
        - 파일 업로드 이벤트 처리

    - SQS / SNS
        - 비동기 이벤트 처리

---

## 한 줄 정리

- Lambda = "서버 없이 이벤트 기반으로 실행되는 코드"

---

- 참고

    - 짧고 가벼운 작업에 적합
    - 상태 없는(stateless) 구조