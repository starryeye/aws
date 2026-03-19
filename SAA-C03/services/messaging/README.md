## SNS vs SQS vs EventBridge

| 구분 | SQS | SNS | EventBridge |
|---|---|---|---|
모델 | Queue | Pub/Sub | Event Bus |
성격 | Command | Notification | Event (Fact) |
전달 방식 | Pull | Push | Rule 기반 |
트리거 | API 호출 | API 호출 | AWS 이벤트 + API |
필터링 | 거의 없음 | 일부 가능 | 매우 강력 |
구조 | 단일 소비 | Fan-out | Rule 기반 Fan-out |
재처리 | 가능 | 제한적 | 제한적 |
순서 보장 | FIFO만 | ❌ | ❌ |
목적 | 작업 처리 | 알림 전파 | 이벤트 라우팅 |
대표 사용 | 비동기 작업 | 알림/브로드캐스트 | 이벤트 기반 아키텍처 |

---
  
구분
- 복잡한 이벤트 흐름 → EventBridge
- 단순 알림 → SNS
- 작업 큐 → SQS