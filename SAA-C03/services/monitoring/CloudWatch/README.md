## CloudWatch

- AWS 리소스의 상태를 모니터링하고 로그 및 알림을 관리하는 서비스

---

## 핵심 개념

- 시스템 상태를 "수집 → 분석 → 알림"하는 서비스

---

## 특징

    - 완전 관리형
    - 실시간 모니터링
    - 로그 수집 가능
    - 알림 및 자동 대응 가능

---

## 주요 기능

---

### 1️⃣ Metrics

- 리소스 상태 수치 데이터

예:

- CPU 사용률
- 네트워크 트래픽
- 디스크 I/O

---

### 2️⃣ Logs

- 애플리케이션 / 시스템 로그 저장

예:

- EC2 로그
- Lambda 로그
- 애플리케이션 로그

---

### 3️⃣ Alarms

- 특정 조건 만족 시 알림 발생

예:

- CPU > 80% → 알림
- 에러 발생 → 알림

---

### 4️⃣ Events (EventBridge로 확장됨)

- 특정 이벤트 발생 시 자동 실행

예:

- EC2 상태 변경 → Lambda 실행

---

### 5️⃣ Dashboard

- 메트릭 시각화

---

## 동작 흐름

    AWS 리소스 → Metrics / Logs 수집
                ↓
            CloudWatch
                ↓
            Alarm / 대응

---

## 특징 정리

- 인프라 모니터링
- 로그 관리
- 자동 알림

---

## CloudWatch vs Performance Insights

| 구분 | CloudWatch | Performance Insights |
|---|---|---|
대상 | 전체 인프라 | DB |
분석 단위 | Metric | Query |
목적 | 상태 모니터링 | 성능 분석 |

---

## 사용 케이스

- 서버 상태 확인
- 로그 분석
- 장애 알림
- Auto Scaling 트리거

---

## 한 줄 정리

- CloudWatch = "AWS 리소스 상태를 모니터링하고 알림까지 처리하는 서비스"