## Kinesis Data Streams

- 실시간으로 데이터를 수집하고 처리할 수 있는 스트리밍 서비스

---

## 핵심 개념

- 데이터를 실시간으로 받아서 직접 처리
- Producer → Stream → Consumer 구조

---

## 특징

    - 실시간 스트리밍 처리
    - 높은 처리량 (High throughput)
    - 데이터 재처리 가능 (Replay)
    - 사용자 정의 처리 가능

---

## 동작 흐름

    Producer (앱 / 로그)
        ↓
    Kinesis Data Stream
        ↓
    Consumer (Lambda / EC2 / Analytics)

---

## 주요 개념

---

### 1️⃣ Shard

- 데이터 처리 단위

👉 성능 기준

- 1 shard
    - Write: 1MB/sec
    - Read: 2MB/sec

---

### 2️⃣ Record

- 스트림에 들어가는 데이터 단위

---

### 3️⃣ Producer

- 데이터를 보내는 주체

---

### 4️⃣ Consumer

- 데이터를 읽어서 처리

---

## 특징 정리

- 실시간 처리 가능
- 데이터 저장 (기본 24시간 ~ 최대 7일+)
- 여러 Consumer가 동일 데이터 처리 가능

---

## 사용 케이스

- 실시간 로그 분석
- 실시간 데이터 처리
- IoT 데이터 처리
- 이벤트 스트리밍

---

## Kinesis Data Streams vs Firehose

| 구분 | Data Streams | Firehose |
|---|---|---|
처리 | 직접 처리 | 자동 전달 |
실시간성 | 실시간 | 준실시간 |
유연성 | 매우 높음 | 낮음 |
관리 | 필요 | 없음 |
재처리 | 가능 | 불가 |

---

## 한 줄 정리

- Data Streams = "실시간 데이터를 직접 처리하는 스트리밍 플랫폼"