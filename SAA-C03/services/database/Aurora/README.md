## Aurora
- AWS 에서 제공하는 고성능 RDBMS (RDS 기반)
  - Aurora MySQL, Aurora PostgreSQL 등
  - Aurora는 RDS 기능을 대부분 지원하면서, 내부적으로 더 진화된 DB이다

- 특징
  - 분산 스토리지 구조 (Shared Storage)
    - 3개의 AZ 에 6개의 복제본을 자동으로 저장
      - storage 자동 확장
      - 기본적으로 Multi AZ 환경 제공
  - 고성능
    - MySQL 대비 최대 5배 성능

- 기능
  - Global Database
    - Primary region + Secondary region 구성
    - 다른 리전에 read-only DB 제공
    - DR (재해 복구) 및 글로벌 읽기 성능 최적화

  - Auto Scaling
    - Aurora Replica(읽기 전용 DB) 자동 확장/축소
    - CPU, connection 수, replica lag 등을 기준으로 조절

  - Reader Endpoint
    - 여러 read replica를 하나의 endpoint로 제공
    - 읽기 트래픽 자동 분산

  - Failover
    - 장애 발생 시 수 초 내 자동 전환

  - Serverless v2
    - 온디맨드 자동 확장형 데이터베이스로..
    - 트래픽에 따라 용량(Compute)이 자동으로 실시간 확장/축소


- 참고. global database 기능
- write
  - Primary Region 에서만 가능
    - 서울 region
      - writer.cluster-xxx.ap-northeast-2.rds.amazonaws.com
      - reader.cluster-xxx.ap-northeast-2.rds.amazonaws.com
- read
  - 각 Region 에서 가능
    - 도쿄 region
      - reader.cluster-xxx.ap-northeast-1.rds.amazonaws.com
- Secondary Region
  - 기본적으로 read-only
- 장애 발생 시 (DR)
  - Secondary Region 을 Primary 로 승격 → write 가능