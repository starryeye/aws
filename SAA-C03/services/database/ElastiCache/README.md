## ElastiCache

- AWS에서 제공하는 fully managed in-memory database
    - Redis, Memcached 지원

- 특징
    - 메모리 기반 (in-memory)
        - 디스크가 아닌 메모리에 데이터 저장
        - 매우 빠른 응답 속도 (sub-millisecond)
    - 완전 관리형
        - 인프라, 패치, 장애 복구 AWS가 처리
    - 캐싱 전용
        - DB 부하 감소 및 성능 향상 목적

---

- 데이터 구조
    - Key-Value 기반
    - (Redis)
        - String, List, Set, Sorted Set, Hash 등 다양한 자료구조 지원
    - (Memcached)
        - 단순 key-value 구조

---

- 기능
    - Cluster Mode (Redis)
        - 데이터를 여러 shard로 분산 저장
        - 수평 확장 가능

    - Multi AZ
        - Primary + Replica 구성
        - 장애 발생 시 자동 failover

    - Read Replica (Redis)
        - 읽기 전용 replica 제공
        - 읽기 성능 향상

    - Auto Scaling
        - shard / node 단위로 확장 가능 (Redis)

    - Backup / Restore (Redis)
        - snapshot 기반 백업 (RDB)
        - AOF(Append Only File) 기반 지속성 옵션

---

- Redis vs Memcached

    - Redis
        - 다양한 자료구조 지원
        - persistence 지원
        - replication / failover 지원
        - 대부분의 경우 사용

    - Memcached
        - 단순 key-value
        - multi-thread 기반
        - persistence 없음
        - 단순 캐시 용도

---

## 한 줄 정리

- ElastiCache = "초고속 메모리 캐시 (DB 부하 감소용)"

---

- 참고
    - endpoint 구조
        - Redis
            - Primary Endpoint (write)
            - Reader Endpoint (read)
            - Node Endpoint (개별 노드)
        - Memcached
            - cluster endpoint 제공 (client-side sharding)

    - 특징
        - 캐시이므로 데이터 영속성이 기본적으로 보장되지 않음
        - (Redis는 옵션으로 persistence 가능)