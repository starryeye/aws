## Glue

- AWS에서 제공하는 서버리스 ETL (Extract, Transform, Load) 서비스
    - 데이터를 추출 → 변환 → 저장
    - 분석 기능은 없다.

---

## 핵심 개념

- 데이터 파이프라인 자동화
- 코드 없이 또는 간단한 코드로 데이터 처리 가능

---

## 특징

    - 서버리스 (Serverless)
    - 자동 스케일링
    - ETL 작업 자동화
    - 다양한 데이터 소스 지원

---

## 주요 기능

---

### 1️⃣ Glue Job

- 실제 ETL 작업 수행

    - Spark 기반
    - Python / Scala 지원

---

### 2️⃣ Glue Crawler

- 데이터 구조 자동 분석

👉 S3 데이터 스캔 → 스키마 자동 생성

---

### 3️⃣ Glue Data Catalog

- 테이블 메타데이터 저장소

👉 Athena / Redshift Spectrum에서 사용

---

### 4️⃣ Glue Studio

- GUI 기반 ETL 구성

---

## 동작 흐름

    데이터 (S3, RDS 등)
        ↓
    Glue Crawler (스키마 생성)
        ↓
    Data Catalog 저장
        ↓
    Glue Job (ETL 처리)
        ↓
    결과 저장 (S3 / Redshift 등)

---

## 특징 정리

- 데이터 이동 + 변환
- 서버리스 ETL
- 메타데이터 관리

---

## 사용 케이스

- 데이터 정제
- 로그 처리
- 데이터 웨어하우스 적재
- ETL 파이프라인 구축

---

## Glue vs EMR vs Athena

| 구분 | Glue | EMR | Athena |
|---|---|---|---|
역할 | ETL | 데이터 처리 | 쿼리 |
구조 | 서버리스 | 클러스터 | 서버리스 |
데이터 | S3 등 | S3/HDFS | S3 |

---

## 한 줄 정리

- Glue = "데이터를 추출, 변환, 저장하는 서버리스 ETL 서비스"