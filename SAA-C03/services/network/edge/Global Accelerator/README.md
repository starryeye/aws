## Global Accelerator

- AWS에서 제공하는 글로벌 네트워크 가속 서비스
    - 전 세계 사용자 트래픽을 AWS 글로벌 네트워크로 빠르게 라우팅

---

- 특징
    - Anycast IP 제공
        - 하나의 고정 IP로 전 세계에서 동일하게 접근 가능
    - 초저지연 (Low Latency)
        - 가장 가까운 Edge Location으로 연결 후 AWS backbone 사용
    - 고가용성
        - 여러 Region / AZ로 트래픽 분산
    - 빠른 장애 복구
        - 헬스 체크 기반으로 자동 failover

---

- 구성 요소

    - Accelerator
        - 고정 Anycast IP 2개 제공

    - Listener
        - 포트 및 프로토콜 정의 (TCP / UDP)

    - Endpoint Group
        - Region 단위 그룹

    - Endpoint
        - 실제 대상 (ALB, NLB, EC2, EIP 등)

---

- 동작 흐름

  Client → Anycast IP
  → 가장 가까운 Edge Location
  → AWS 글로벌 네트워크 (backbone)
  → 최적의 Region Endpoint

---

- 주요 기능

    - 트래픽 라우팅 최적화
        - latency 기반 라우팅

    - 헬스 체크
        - 비정상 endpoint 자동 제외

    - Weight / Traffic Dial
        - Region 간 트래픽 비율 조절

---

## CloudFront vs Global Accelerator

| 구분 | CloudFront | Global Accelerator |
|---|---|---|
계층 | L7 (HTTP) | L4 (TCP/UDP) |
목적 | 캐싱 | 네트워크 가속 |
IP | 변경 가능 | 고정 IP |
캐싱 | 있음 | 없음 |
대상 | 정적/동적 콘텐츠 | 모든 TCP/UDP 트래픽 |

---

## 사용 케이스

- 글로벌 게임 서버 (UDP)
- 실시간 금융 서비스
- multi-region failover
- 고정 IP 필요 서비스

---

## 한 줄 정리

- Global Accelerator = "글로벌 네트워크를 통해 TCP/UDP 트래픽을 빠르게 전달하는 서비스"

---

- 참고

    - 캐싱 필요 → CloudFront
    - 고정 IP + TCP/UDP 최적화 → Global Accelerator