# TM 장비 (Traffic Manager)

## 1. 개요
TM(Traffic Manager) 장비는 네트워크 트래픽을 **효율적으로 분산, 제어, 관리**하기 위해 사용하는 장비이다.  
주로 대규모 서비스 환경에서 **부하 분산(Load Balancing)**, **트래픽 최적화**, **고가용성(High Availability)** 확보를 위해 도입된다.  

---

## 2. 주요 기능

### 2.1 트래픽 분산 (Load Balancing)
- 여러 서버로 들어오는 요청을 균등하게 분산
- 특정 서버 과부하 방지
- Round Robin, Least Connection, IP Hash 등의 알고리즘 제공

### 2.2 장애 대응 (Failover)
- 특정 서버나 서비스에 장애 발생 시 다른 서버로 자동 우회
- 무중단 서비스 제공

### 2.3 보안 기능
- SSL 오프로딩(SSL 암복호화 처리 대행)
- DDoS 방어 및 트래픽 제어
- 비정상 트래픽 필터링

### 2.4 트래픽 최적화
- 캐싱(Caching) 기능으로 응답 속도 개선
- 압축(Compression)을 통한 대역폭 절약
- 세션 유지(Session Persistence)

---

## 3. 아키텍처 예시

```text
[Client] → [TM 장비] → [WAS / Application Server] → [DB Server]
