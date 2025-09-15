# API vs RESTful API

## 1. API란?
- **API (Application Programming Interface)**  
  - **정의**: 한 소프트웨어가 다른 소프트웨어의 기능이나 데이터를 **호출·사용할 수 있게 해주는 인터페이스**.
  - **형태**: 함수 호출, 라이브러리, HTTP 요청/응답 등 **형식 제한 없음**.
  - 예: Java의 `JDBC`, Windows OS의 파일 I/O API, HTTP 기반의 OpenWeather API 등.

---

## 2. RESTful API란?
- **REST(Representational State Transfer)** 원칙을 따르는 **웹 기반 API**.
- **조건** (주요 제약 조건)
  1. **Client-Server**: 클라이언트와 서버가 역할을 명확히 분리
  2. **Stateless**: 요청 간 서버는 상태를 저장하지 않음
  3. **Cacheable**: 응답이 캐싱될 수 있어야 함
  4. **Uniform Interface**: 리소스(데이터)를 **URI**로 식별, **HTTP 메서드**로 행위 표현  
     - GET(조회), POST(생성), PUT/PATCH(수정), DELETE(삭제)
  5. **Layered System**: 중간 계층(프록시·로드밸런서 등) 존재 가능
  6. (선택) **Code on Demand**: 서버가 클라이언트에 코드 전송 가능

---

## 3. 차이점 정리

| 구분 | API | RESTful API |
|------|----|------------|
| **범위** | 모든 종류의 소프트웨어 간 인터페이스 | **웹에서 HTTP를 이용**하는 특정 스타일의 API |
| **규칙** | 형식·프로토콜 자유 (SOAP, RPC, gRPC 등) | REST 아키텍처 제약 조건을 준수 |
| **데이터 포맷** | 제한 없음 (XML, JSON, 이진 등) | 보통 JSON(권장), XML도 가능 |
| **메서드** | 개발자 정의 | HTTP 메서드 표준 사용 (GET/POST/PUT/DELETE) |
| **상태 유지** | 세션 유지 가능 | **Stateless**(서버가 클라이언트 상태 저장 X) |

---

## 4. 간단 예시
### 일반 API
- 은행 내부 Java 라이브러리에서 `transferMoney(from, to, amount)` 메서드 제공 → 프로그램끼리 직접 호출.

### RESTful API
- `POST /accounts/transfer`  
  Request Body:
  ```json
  { "from": "123", "to": "456", "amount": 10000 }
