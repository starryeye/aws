## AWS Direct Connect Gateway (DX Gateway)

- AWS에서 제공하는 **네트워크 연결 확장 서비스**
- Direct Connect를 통해 연결된 온프레미스 환경을 **여러 VPC 및 여러 리전에 연결 가능하게 하는 중간 허브**

---

### Direct Connect 와의 관계

- Direct Connect = 물리적 전용선 연결
- Direct Connect Gateway = 그 연결을 **여러 VPC로 확장하는 논리적 리소스**

---

### 주요 기능

#### 1. 멀티 VPC 연결
- 하나의 Direct Connect로 여러 VPC 연결 가능

#### 2. 멀티 리전 지원
- 서로 다른 리전의 VPC 연결 가능

#### 3. 온프레미스 연결 단순화
- 여러 VPC를 하나의 DX로 통합 연결

---

### 기본 구조

```text
On-Prem
   ↓
Direct Connect
   ↓
Direct Connect Gateway
   ↓
VPC A
VPC B
VPC C
```
- 특징
  - VPC <--> VPC 통신 불가능

---

### Transit Gateway 와 함께 쓴다면..

On-Prem
↓
Direct Connect
↓
Direct Connect Gateway
↓
Transit Gateway
↓
VPC A / VPC B / VPC C

- 특징
  - Transit Gateway를 통해 내부 VPC 간 통신 가능
  - 중앙 라우팅 제어
     - Transit Gateway Route Table로 트래픽 제어 가능
     - 특정 VPC 간 통신 허용/차단
     - 네트워크 분리 (Segmentation)