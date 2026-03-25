## DynamoDB

- AWS에서 제공하는 fully managed NoSQL database
    - key-value 및 document 데이터 모델 지원
        - 스키마가 고정되지 않는 유연한 데이터 구조

- 특징
    - 서버리스 (Serverless)
        - 서버 관리 불필요, 자동 확장
    - 고성능
        - single-digit millisecond latency
    - 완전 관리형
        - 인프라, 패치, 스케일링 AWS가 처리

---

- 데이터 구조
    - Table
        - PK (Partition Key)
        - SK (Sort Key, optional)
    - schema-less (유연한 구조)

---

- 기능
    - Auto Scaling
        - 트래픽에 따라 read/write capacity 자동 조절

    - Global Table
        - 여러 리전에 걸쳐 multi-master 구성
            - eventual consistency 기반 (last writer wins) 으로 하나의 DB 처럼 싱크됨
        - 모든 리전에서 read/write 가능
        - 글로벌 서비스 및 DR 용도

    - DAX (DynamoDB Accelerator)
        - in-memory cache
        - 읽기 성능 향상 (microsecond 수준)

    - TTL (Time To Live)
        - 일정 시간 후 데이터 자동 삭제

    - Streams
        - 데이터 변경 이벤트를 스트림으로 제공
        - Lambda 등과 연동 가능

    - PITR (Point-in-Time Recovery)
        - 최대 35일간 데이터 시점 복구 가능
          - AWS Backup 은 그보다 훨씬 길다.

---

- 일관성 모델
    - Eventually Consistent (기본)
    - Strongly Consistent (옵션)
        - global table 기능과 함께 사용 불가능

---

## 한 줄 정리

- DynamoDB = "완전 서버리스 + 초고속 + 글로벌 write 가능한 NoSQL DB"

---

- 참고
    - endpoint 구조
        - 리전별 단일 endpoint 제공
            - writer / reader endpoint 구분 없음
            - 내부적으로 AWS가 자동으로 분산 처리
            - global table 기능을 활성화하면...
                - 모든 리전의 테이블 및 데이터가 동기화 된다.