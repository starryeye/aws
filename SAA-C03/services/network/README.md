## Route53 vs CloudFront vs Global Accelerator vs API Gateway

| 구분 | Route53 | CloudFront | Global Accelerator | API Gateway |
|---|---|---|---|---|
| 역할 | DNS | CDN | 네트워크 가속 | API 관리 |
| 핵심 기능 | 도메인 → IP 매핑 | 콘텐츠 캐싱 | 글로벌 네트워크 최적화 | API 요청 처리 |
| 계층 | DNS | L7 (HTTP/HTTPS) | L4 (TCP/UDP) | L7 (HTTP/WebSocket) |
| 캐싱 | ❌ | ⭕ | ❌ | ⭕ (REST API) |
| IP | 반환만 | ❌ | ⭕ (고정 Anycast IP) | ❌ |
| 라우팅 방식 | DNS 기반 | 콘텐츠 기반 | 네트워크 기반 | API 경로 기반 |
| 주요 대상 | 모든 서비스 | 웹 (정적/동적) | TCP/UDP 서비스 | API (Lambda/ALB 등) |
| 사용 목적 | 어디로 보낼지 결정 | 빠르게 전달 | 빠르게 연결 | API 진입점 |
| 대표 키워드 | Routing | Caching | Latency | API Management |

---

## 🔥 한 줄 핵심

- Route53 = "어디로 보낼지 결정"
- CloudFront = "콘텐츠를 빠르게 전달"
- Global Accelerator = "네트워크 경로를 최적화"
- API Gateway = "API 요청을 관리하고 처리"

---

## 🔥 핵심 구분 감각

- Route53 → 길찾기, "DNS 레벨"
- CloudFront → 빠른 배달, "콘텐츠 레벨"
- Global Accelerator → 빠른 길, "네트워크 레벨"
- API Gateway → 입구와 통제, "애플리케이션(API) 레벨"