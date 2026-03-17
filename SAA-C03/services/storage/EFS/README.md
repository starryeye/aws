## EFS
- NFS(Network File System) storage
  - 여러 EC2 인스턴스에서 동시에 접근 가능 (동시에 같은 파일 시스템을 공유)
- 다중 AZ 에서 동작 가능
- Linux 기반 파일공유 프로토콜인 NFS 만 지원한다.
- 용량 자동 확장 (Auto scaling)
- EFS Intelligent-Tiering 기능 존재
  - 자주 접근하지 않는 파일을 EFS IA(Infrequent Access) 스토리지 클래스로 이동
    - EFS IA 도 즉시 접근 가능함
