# Resin `error-page`와 500 에러 처리

---

## 1. 개요
- Java/Servlet 기반 프로젝트에서 실행 중 예외(Exception)가 발생하면 기본적으로 **500 Internal Server Error**가 발생한다.
- `resin.xml` 또는 `web.xml`에 `error-page`를 설정하면, WAS가 해당 예외나 상태 코드에 맞는 페이지로 포워딩한다.
- 즉, **try문 실행 중 예외가 catch에서 처리되지 않으면 → WAS가 감지 → error-page로 이동**하는 구조이다.

---

## 2. Resin 설정 예시
```xml
<web-app>
  <!-- 500 Internal Server Error 발생 시 -->
  <error-page>
    <error-code>500</error-code>
    <location>/error/500.jsp</location>
  </error-page>

  <!-- 특정 예외 전용 처리 -->
  <error-page>
    <exception-type>java.lang.NullPointerException</exception-type>
    <location>/error/npe.jsp</location>
  </error-page>
</web-app>
