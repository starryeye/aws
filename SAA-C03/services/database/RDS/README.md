## RDS
- AWS 에서 제공하는 managed RDBMS 서비스
    - MySQL, PostgreSQL, MariaDB, Oracle, SQL Server 등 지원

- 유형
    - 범용 SSD (gp2, gp3)
    - Provisioned IOPS SSD (io1, io2)
      - high throughput, low latency
      - IOPS (초당 입출력 연산 수) 직접 설정 가능

- 기능
  - Multi AZ 배포
    - Primary DB + Standby DB 구성
      - Standby DB 는 Primary DB 동기 복제함
      - Standby DB 는 읽기 트래픽 처리 불가 (failover 전용)
    - 장애 시 자동으로 standby DB 를 Primary DB 로 전환
      - 고가용성 확보용

  - Multi AZ DB cluster 배포
    - Primary + Standby 2개
    - reader endpoint 제공 (Standby 에서 read 가능)
      - 같은 리전에서 고가용성, 읽기 성능 개선용

  - Read Replica
    - 읽기 전용 DB(비동기 복제) 를 추가
      - 읽기 성능 개선
      - 수동으로 primary 승격 가능

  - Cross Region Read Replica
    - 다른 리전에 read replica 생성함으로써 DR (재해 복구) 용도

  - RDS Proxy
    - application, DB 간 connection 을 재사용하고 관리하여 관련 문제 예방용
    - Lambda / burst 트래픽 환경에서 효과적

  - RDS Blue/Green 배포
    - blue 와 동기화된 별도의 green 을 생성
    - green 을 test 하고 다운타임 최소화(near zero downtime)하여 트래픽을 green 으로 전환해주는 기능