## EBS
- EC2 에 attach 해서 사용하는 block storage
  - RDS 등 일부 서비스는 내부적으로 사용하지만 직접 attach는 불가
- 단일 AZ 에서만 동작한다.
- low latency, high performance storage 유형 존재
- OS 디스크, 데이터베이스 스토리지에 적합

- 기능
  - EBS Elastic Volume
    - EC2 무중단 볼륨 크기 확장 기능