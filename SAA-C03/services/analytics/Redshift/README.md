## Redshift

- AWS에서 제공하는 데이터 웨어하우스 (Data Warehouse) 서비스
    - 대용량 데이터를 빠르게 분석 (OLAP)

---

## 핵심 개념

- 대용량 데이터 + 분석 + 저장
- 분석용 데이터베이스
- 대량 데이터를 컬럼 기반으로 저장하고 빠르게 조회

---

## 특징

    - 컬럼 기반 저장 (Columnar Storage)
    - 대용량 데이터 분석 최적화
    - MPP (Massively Parallel Processing)
    - SQL 지원

---

## 구조

### 1️⃣ Leader Node

- 쿼리 분배 및 결과 집계

---

### 2️⃣ Compute Node

- 실제 데이터 저장 및 처리

---

## 동작 방식

    Client → Leader Node → Compute Node (병렬 처리)
                           ↓
                        결과 반환

---

## 특징 정리

- OLTP ❌ (트랜잭션용 아님)
- OLAP ⭕ (분석용)
- 대용량 데이터 빠른 집계

---

## 주요 기능

### 1️⃣ Columnar Storage

- 필요한 컬럼만 읽음 → 성능 향상

---

### 2️⃣ Compression

- 데이터 압축 → 저장 비용 절감

---

### 3️⃣ Spectrum

- S3 데이터 직접 조회 가능

---

### 4️⃣ Concurrency Scaling

- 동시 쿼리 처리 확장

---

## 사용 케이스

- 데이터 분석
- BI (Business Intelligence)
- 리포팅
- 로그 분석

---

## Redshift vs RDS vs Athena

| 구분 | Redshift | RDS | Athena |
|---|---|---|---|
용도 | 분석 | 트랜잭션 | 쿼리 |
데이터 | 대용량 | 일반 DB | S3 |
구조 | MPP | 단일 DB | 서버리스 |

---

## 한 줄 정리

- Redshift = "대용량 데이터를 빠르게 분석하는 데이터 웨어하우스"