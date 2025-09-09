# WAS 로그 구분

일반적으로 Java 기반 WAS 환경에서는 로그가 크게 세 가지로 구분된다.

---

## 1. WAS 로그
- 서버 기동/종료, 내부 오류, 리소스 상태 등을 기록한다.  
- 애플리케이션에서 발생한 예외 스택트레이스도 포함된다.  
- 예시 파일
  - Tomcat: `catalina.out`, `catalina.YYYY-MM-DD.log`
  - JBoss/WildFly: `server.log`
  - WebLogic: `AdminServer.log`

---

## 2. stdout / stderr 로그
- **stdout**  
  - `System.out.println()`, `logger.info()` 같은 일반 출력  
  - 개발자가 남긴 메시지 확인에 사용  
- **stderr**  
  - `System.err.println()`이나 에러 발생 시 출력되는 스택트레이스  
  - 오류, 경고 메시지 중심  
- 보통 WAS 로그에 합쳐지거나 `stdout.log`, `stderr.log`로 따로 분리되기도 한다.  

---

## 3. Access 로그
- 클라이언트 요청/응답 정보를 기록한다.  
- 요청 URL, HTTP Method, 응답 코드, 처리 시간, User-Agent, IP 등이 포함된다.  
- 예시 파일
  - Tomcat: `localhost_access_log.YYYY-MM-DD.txt`  
- 형식 예시

---

## 정리
- **WAS 로그**: 서버 동작과 애플리케이션 오류  
- **stdout/stderr**: 개발자가 출력한 메시지와 실행 중 에러  
- **Access 로그**: 클라이언트 요청/응답 기록  

보통 이 세 가지 로그를 분리해 관리한다.