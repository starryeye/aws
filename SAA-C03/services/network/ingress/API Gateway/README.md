## API Gateway

- AWS에서 제공하는 API 관리 서비스
    - HTTP / REST / WebSocket API 생성 및 관리

---

- 특징
    - 서버리스
        - 서버 없이 API 생성 가능
    - 완전 관리형
        - 확장, 배포 자동 처리
    - 다양한 백엔드 연동
        - Lambda, EC2, ECS, ALB, DynamoDB 등
    - 보안 기능 내장
        - 인증/인가, throttling

---

- 유형

    - AWS Gateway REST API
        - 가장 기능 풍부
        - API Key, Usage Plan, 캐싱 지원
        - JWT 인증 기능 지원하지 않음

    - AWS Gateway HTTP API
        - 더 가볍고 저렴
        - 기본적인 API 기능 제공
        - JWT 인증 기능 지원함

    - AWS Gateway WebSocket API
        - 실시간 양방향 통신

---

- 구성 요소

    - Resource
        - URL 경로 (/users, /orders)

    - Method
        - HTTP 메서드 (GET, POST 등)

    - Integration
        - 백엔드 연결 (Lambda, HTTP 등)

    - Stage
        - 배포 환경 (dev, prod)

---

- 동작 흐름

  Client → API Gateway → Backend → 응답

---

- 주요 기능

    - Authentication / Authorization
        - IAM
        - Cognito
        - Custom Authorizer

    - Throttling
        - 요청 제한 (rate limit)

    - Caching
        - 응답 캐싱 (REST API)

    - Transformation
        - 요청/응답 변환 (Mapping Template)

    - Edge-optimized
        - 전세계 사용자의 API 응답 속도를 줄여준다.
        - CloudFront 네트워크를 활용한다.

---

- 통합 서비스

    - Lambda
        - 서버리스 API

    - ALB / EC2
        - 기존 애플리케이션 연결

    - DynamoDB
        - 직접 연동 가능

---

- 배포

    - Stage 기반 배포
    - Canary Deployment 지원

---

## 사용 케이스

- 서버리스 API (Lambda 연동)
- 모바일 / 웹 백엔드
- 마이크로서비스 API 게이트웨이

---

## 한 줄 정리

- API Gateway = "클라이언트와 백엔드 사이의 API 관리 및 진입점"

---

- 참고

    - 간단/저렴 → HTTP API
    - 기능 많음 → REST API