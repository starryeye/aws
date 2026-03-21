## CloudFront

- AWS에서 제공하는 CDN (Content Delivery Network)
    - 전 세계 Edge Location을 통해 콘텐츠를 캐싱하여 빠르게 전달

---

- 특징
    - 저지연 (Low Latency)
        - 사용자와 가까운 Edge Location에서 응답
    - 캐싱 (Caching)
        - 콘텐츠를 캐싱하여 origin 부하 감소
    - 글로벌 서비스
        - 전 세계 사용자 대상 서비스 최적화
    - 보안 강화
        - HTTPS, WAF, Shield 연동

---

- 구성 요소

    - Distribution
        - CloudFront 설정 단위

    - Origin
        - 원본 서버
        - 예:
            - S3
            - EC2
            - ALB
            - API Gateway

    - Edge Location
        - 캐시가 저장되는 위치

---

- 동작 흐름

  Client → Edge Location (Cache 확인)
  → Cache hit → 바로 응답
  → Cache miss → Origin 요청 → 캐싱 후 응답

---

- 캐싱

    - TTL (Time To Live)
        - 캐시 유지 시간

    - Cache Key
        - URL, Header, Cookie 기반 캐싱

---

- Origin 유형

    - S3 Origin
        - 정적 파일 (이미지, JS, CSS)

    - Custom Origin
        - EC2 / ALB / API 서버

---

- 주요 기능

    - OAI / OAC
        - S3를 private하게 접근 가능

    - Signed URL / Signed Cookie
        - 특정 사용자만 접근 허용

    - HTTPS 지원
        - TLS 인증서 적용

    - Compression
        - Gzip / Brotli 지원

---

- 보안

    - AWS WAF 연동
    - AWS Shield (DDoS 방어)

---

- 캐시 무효화

    - Invalidation
        - 특정 파일 캐시 제거

---

### 한 줄 정리

- CloudFront = "전 세계 Edge에서 캐싱하여 빠르게 콘텐츠를 전달하는 CDN"

---

- 참고

    - 정적 콘텐츠
      - Client → CloudFront → S3
    - 동적 콘텐츠
      - Client → CloudFront → ALB → EC2