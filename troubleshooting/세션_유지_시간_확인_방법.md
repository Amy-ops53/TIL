# 세션(Session) 유지 시간 확인 방법

---

## 1. 서버/WAS 설정 확인
세션 만료 시간은 보통 **서버(WAS) 설정 파일**에서 관리된다.

- **Tomcat**
  ```xml
  <session-config>
      <session-timeout>30</session-timeout> <!-- 분 단위 -->
  </session-config>
  ```
  → 위 설정은 **30분 동안 요청이 없으면 세션 만료**됨.

- **Resin, WebLogic, JBoss 등**도 비슷하게 설정 파일에서 관리 가능.

---

## 2. 코드에서 확인 (Java/Spring 예시)
- Java EE(Servlet)
  ```java
  int timeout = session.getMaxInactiveInterval(); 
  System.out.println("세션 유지 시간(초): " + timeout);
  ```
  - 반환값은 **초 단위**.
  - `setMaxInactiveInterval(int seconds)`로 코드에서 변경 가능.

- Spring Boot
  ```properties
  server.servlet.session.timeout=30m
  ```

---

## 3. 브라우저(클라이언트)에서 확인
- 세션 ID는 보통 **쿠키(JSESSIONID)** 형태로 브라우저에 저장된다.
- 쿠키의 **만료 시간**을 확인하면 브라우저 종료 시까지 유지되는지(세션 쿠키) 또는 특정 시각까지 유지되는지 알 수 있다.
- 하지만 최종 만료 여부는 **서버 세션 정책**에 의해 결정된다.

---

## 4. 운영 환경에서 확인
- 로그인 후 **아무 요청 없이 대기** → 세션이 만료되면 다음 요청 시 로그인 페이지로 리다이렉트되거나 401/403 에러 발생.
- 운영 환경에서는 모니터링 툴(APM)이나 **WAS 로그**로 세션 만료 이벤트를 추적할 수 있다.

---

## 요약
1. **서버 설정 파일** (web.xml, application.properties 등) 확인.  
2. **코드** (`HttpSession#getMaxInactiveInterval`)로 확인.  
3. **쿠키(JSESSIONID)** 확인.  
4. **실제 동작 테스트** 또는 **운영 모니터링**으로 확인.  
