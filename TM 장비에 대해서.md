# TM 장비 (Traffic Manager)

## 1. 개요
TM(Traffic Manager) 장비는 네트워크 환경에서 **트래픽을 효율적으로 분산하고, 서비스 가용성과 안정성을 보장**하기 위해 사용되는 장비이다.  
일반적으로 L4/L7 스위치의 기능을 포괄하거나 확장한 개념으로, **부하 분산(Load Balancing), 트래픽 제어, 보안 강화, 장애 대응** 등을 수행한다.  

---

## 2. 주요 기능

### 2.1 부하 분산 (Load Balancing)
- **목적**: 서버 간 요청을 균등하게 배분하여 과부하 방지  
- **알고리즘 종류**
  - **Round Robin**: 요청을 순차적으로 서버에 분배
  - **Least Connection**: 연결 수가 가장 적은 서버로 요청 전달
  - **IP Hash**: 클라이언트 IP 기반으로 특정 서버에 고정 매핑
  - **Weighted Round Robin**: 서버 성능에 따라 가중치 부여 후 분배

### 2.2 장애 대응 (Failover & Health Check)
- 서버 상태를 실시간으로 모니터링 (Health Check)
- 비정상 서버 탐지 시 트래픽을 다른 정상 서버로 우회
- 무중단 서비스 제공 가능

### 2.3 보안 기능
- **SSL Offloading**
  - 암·복호화 작업을 서버 대신 TM 장비가 수행
  - 서버 부하 감소, 인증서 관리 단순화
- **DDoS 대응**
  - 비정상적인 대량 요청을 차단
  - Rate Limiting, Connection Limit 등의 정책 적용 가능
- **ACL / Firewall 기능**
  - 특정 IP, 포트, 프로토콜 기반 접근 제어

### 2.4 트래픽 최적화
- **캐싱(Caching)**: 동일 요청에 대해 응답 데이터를 TM 장비에서 직접 제공 → 서버 부하 감소
- **압축(Compression)**: 응답 데이터 크기를 줄여 네트워크 효율 개선
- **세션 지속성(Session Persistence, Sticky Session)**
  - 동일 클라이언트 요청을 항상 같은 서버로 전달
  - 로그인, 장바구니 기능 등에 필수

---

## 3. 아키텍처 예시

```text
[ Client ]
    ↓
[ TM 장비 ]
    ↓ (부하 분산/보안/최적화)
[ Web / WAS Server Pool ]
    ↓
[ Database ]
