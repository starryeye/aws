## ELB (Elastic Load Balancing)

- AWS에서 제공하는 트래픽 분산 서비스
    - 여러 대상(EC2, ECS, Lambda 등)에 트래픽을 분산

---

- 특징
    - 고가용성
        - 여러 AZ에 걸쳐 트래픽 분산
    - 자동 확장
        - 트래픽 증가 시 자동 처리
    - 헬스 체크
        - 비정상 인스턴스 자동 제외
    - 완전 관리형
        - 인프라 관리 불필요

---

- 유형

    - ALB (Application Load Balancer)
        - Layer 7 (HTTP/HTTPS)
        - 특징
            - 경로 기반 라우팅 (/api, /admin)
            - 호스트 기반 라우팅 (domain)
            - WebSocket 지원
            - WAF(웹 어플리케이션 방화벽)에 연결 가능 (ALB 만 가능)
        - 사용 케이스
            - 웹 애플리케이션, API 서버

    - NLB (Network Load Balancer)
        - Layer 4 (TCP/UDP)
        - 특징
            - 매우 높은 성능
            - 초저지연 (ultra low latency)
            - static IP 지원
        - 사용 케이스
            - 게임 서버, 실시간 서비스

    - GWLB (GLB, Gateway Load Balancer)
        - Layer 3/4
        - 특징
            - 보안 장비 연동 (Firewall, IDS/IPS)
        - 사용 케이스
            - 네트워크 보안 처리

    - CLB (Classic Load Balancer)
        - 구버전 (legacy)
        - 신규 사용 비추천

---

- 주요 기능

    - Listener
        - 요청을 받아들이는 포트/프로토콜

    - Target Group
        - 트래픽을 전달할 대상 그룹

    - Health Check
        - 대상 상태 확인

---

- 동작 흐름 예시

  Client → ELB → Target Group → EC2

---

- 보안

    - Security Group (ALB/NLB 일부)
    - TLS/SSL termination 지원

---

- 고급 기능

    - Sticky Session (Session Affinity)
        - 동일 사용자 요청을 동일 서버로 전달

    - Cross-Zone Load Balancing
        - AZ 간 트래픽 균등 분산

    - Auto Scaling 연동
        - ASG(auto scaling group) 와 함께 자동 확장

---

## 한 줄 정리

- ELB = "트래픽을 여러 서버로 분산하여 가용성과 성능을 높이는 서비스"

---

- 참고

    - ALB = HTTP 레벨 제어
    - NLB = 고성능 TCP 처리
    - GWLB = 보안 장비용