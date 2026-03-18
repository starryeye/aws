## Route53 vs CloudFront vs Global Accelerator

| 구분 | Route53 | CloudFront | Global Accelerator |
|---|---|---|---|
| 역할 | DNS | CDN | 네트워크 가속 |
| 핵심 기능 | 도메인 → IP 매핑 | 콘텐츠 캐싱 | 글로벌 네트워크 최적화 |
| 계층 | DNS | L7 (HTTP/HTTPS) | L4 (TCP/UDP) |
| 캐싱 | ❌ | ⭕ | ❌ |
| IP | 반환만 | ❌ | ⭕ (고정 Anycast IP) |
| 라우팅 방식 | DNS 기반 | 콘텐츠 기반 | 네트워크 기반 |
| 주요 대상 | 모든 서비스 | 웹 (정적/동적) | TCP/UDP 서비스 |
| 사용 목적 | 어디로 보낼지 결정 | 빠르게 전달 | 빠르게 연결 |
| 대표 키워드 | Routing | Caching | Latency |

---

## 한 줄 핵심

- Route53 = "어디로 보낼지 결정"
- CloudFront = "콘텐츠를 빠르게 전달"
- Global Accelerator = "네트워크 경로를 최적화"