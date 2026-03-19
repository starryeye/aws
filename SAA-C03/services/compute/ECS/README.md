## ECS (Elastic Container Service)

- AWS에서 제공하는 컨테이너 오케스트레이션 서비스
    - Docker 컨테이너 실행 및 관리

---

- 특징
    - 완전 관리형
        - Kubernetes 없이 컨테이너 운영 가능
    - AWS 서비스와 강력한 통합
        - ALB, CloudWatch, IAM 등
    - 간단한 구조
        - 비교적 학습 난이도 낮음

---

- 실행 방식

    - EC2 Launch Type
        - EC2 인스턴스 위에서 컨테이너 실행
        - 세부 설정 가능
        - 직접 서버 관리 필요

    - Fargate Launch Type
        - 서버리스 컨테이너 실행
        - 완전 관리형 서비스(EC2 관리 필요 없음)
          - AWS 가 scaling 관리하여 예측 불가 트래픽을 유연하게 대응

---

- 구성 요소

    - Cluster
        - 컨테이너가 실행되는 논리적 그룹

    - Task Definition
        - 컨테이너 실행 설정 (이미지, CPU, Memory 등)

    - Task
        - 실행 중인 컨테이너 인스턴스

    - Service
        - Task를 유지/관리 (Auto Scaling, Load Balancing)

---

- 네트워크

    - awsvpc 모드
        - 각 Task에 ENI 할당
        - VPC 내에서 독립 네트워크

---

- 배포

    - Rolling Update
        - 점진적 배포

    - Blue/Green (CodeDeploy 연동)
        - 무중단 배포

---

- 확장

    - Auto Scaling
        - CPU / Memory 기반
        - 요청 수 기반 (ALB 연동)

---

- 로드밸런싱

    - ALB / NLB와 연동
    - Service 단위로 트래픽 분산

---

- 보안

    - IAM Role
        - Task Role (컨테이너 권한)
        - Execution Role (이미지 pull 등)

---

## 한 줄 정리

- ECS = "AWS에서 Docker 컨테이너를 쉽게 실행/관리하는 서비스"

---

- 참고

    - 간단 → ECS
    - 복잡/표준 → EKS (Kubernetes)