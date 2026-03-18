## EC2 (Elastic Compute Cloud)

- AWS에서 제공하는 가상 서버 (IaaS)
    - 원하는 OS, CPU, Memory, Storage 설정 가능

---

- 특징
    - 온디맨드 컴퓨팅
        - 필요할 때 생성, 종료 가능
    - 확장성 (Scalability)
        - Auto Scaling 과 함께 사용
    - 다양한 인스턴스 타입 제공
        - 목적에 따라 선택 가능

---

- 인스턴스 타입

    - General Purpose (범용)
        - t, m 계열
        - 균형 잡힌 성능

    - Compute Optimized
        - c 계열
        - CPU 집약 작업

    - Memory Optimized
        - r, x 계열
        - 대용량 메모리 (DB, 캐시)

    - Storage Optimized
        - i, d 계열
        - 고속 디스크 처리

---

- 구매 옵션

    - On-Demand
        - 사용한 시간만큼 후불 결제
        - 필요할 때 사용, 가장 비쌈

    - Reserved Instance (RI)
        - 1 ~ 3년 약정으로 예약해서 비용 할인

    - Savings Plans
        - 사용량 기반 할인

    - Spot Instance
        - AWS 의 남는 EC2 를 매우싸게 빌리는 방식
        - AWS 가 언제든 회수하여 중단 가능성 있음

---

- 네트워크

    - VPC 내부에서 실행
    - ENI (Elastic Network Interface)
        - 네트워크 인터페이스

    - IP
        - Private IP (기본)
        - Public IP (자동 할당)
        - Elastic IP (고정 IP)

---

- 스토리지

    - EBS
        - 블록 스토리지
        - EC2에 attach

    - Instance Store
        - 로컬 디스크
        - 휘발성

    - EFS
        - 여러 EC2에서 공유 가능 (NFS)

---

- 보안

    - Security Group
        - 인바운드/아웃바운드 허용 규칙 (stateful)

    - Key Pair
        - SSH 접속용 인증

    - IAM Role
        - EC2 → AWS 서비스 접근 권한

---

- 고가용성 / 확장

    - Auto Scaling Group (ASG)
        - 인스턴스 자동 증가/감소

    - Elastic Load Balancer (ELB)
        - 트래픽 분산

---

- 배포 / 초기화

    - AMI (Amazon Machine Image)
        - EC2 템플릿

    - User Data
        - 인스턴스 시작 시 스크립트 실행

---

- 상태

    - running / stopped / terminated

---

### 한 줄 정리

- EC2 = "AWS에서 제공하는 확장 가능한 가상 서버"

---

- 참고

    - EC2는 stateful 서비스 (데이터는 EBS 등에 저장 필요)
    - AZ 단위 리소스 (특정 AZ에 속함)

---

- Placement Group (인스턴스 배치 전략)

- 개념
    - EC2 인스턴스를 물리적으로 어떻게 배치할지 결정하는 전략

- Cluster Placement Group
    - 동일 AZ 내에서 인스턴스를 최대한 가까이 배치
    - 특징
        - 매우 높은 네트워크 성능 (low latency, high throughput)
    - 단점
        - AZ 하나에만 존재 → 가용성 낮음
    - 사용 케이스
        - HPC, Big Data, 고성능 네트워크

- Spread Placement Group
    - 서로 다른 하드웨어에 분산 배치
    - 특징
        - 장애 격리 (fault isolation)
    - 제한
        - 최대 7개 인스턴스 / AZ
    - 사용 케이스
        - critical 시스템 (서버 장애 분산)

- Partition Placement Group
    - 여러 partition으로 나눠서 배치
    - 각 partition은 독립적인 하드웨어
    - 특징
        - 일부 장애 시 전체 영향 최소화
    - 사용 케이스
        - Kafka, HDFS, 분산 시스템

### 핵심 정리

- Cluster = 성능
- Spread = 장애 분산
- Partition = 대규모 분산 시스템

---

### 한 줄 요약

- Placement Group = "성능 vs 가용성을 제어하는 물리 배치 전략"