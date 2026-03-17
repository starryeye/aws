## EFS

- File storage
- NFS(Network File System) storage
    - 여러 EC2 인스턴스에서 동시에 접근 가능 (동시에 같은 파일 시스템을 공유)
    - 범용 파일공유인 점에서 FSx for Lustre 와 비슷하나 성능면에서 좋지 않음
- 다중 AZ 에서 동작 가능
- Linux 기반 파일공유 프로토콜인 NFS 만 지원한다.
- 용량 자동 확장 (Auto scaling)


- 기능
    - EFS Intelligent-Tiering 기능 (EFS Lifecycle Management, 수명 주기 관리)
        - 자주 접근하지 않는 파일을 EFS IA(Infrequent Access) 스토리지 클래스로 이동
        - EFS IA 도 즉시 접근 가능함
    - throughput mode 기능
        - 파일 시스템의 데이터 처리 속도 (읽기/쓰기 성능)를 결정하는 모드이다.
        - Bursting Throughput
            - 기본값, 일반적인 워크로드
            - 파일 시스템 크기에 따라 throughput 자동 증가
        - Provisioned Throughput
            - 파일 시스템 크기와 무관하게 throughput 직접 설정
            - 일정한 고성능 요구에 추천
        - Elastic Throughput
            - 워크로드에 따라 자동으로 throughput 조절
            - 예측하기 어려운 워크로드