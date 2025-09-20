# HTTP 401 Unauthorized 에러

---

## 1. 개요
- **401 Unauthorized**는 클라이언트가 요청한 리소스에 대해 **인증(Authentication)**이 필요하지만,  
  올바른 인증 자격 증명(credential)을 제공하지 않았을 때 발생하는 HTTP 상태 코드이다.
- 주로 로그인/토큰/세션 인증 과정에서 문제가 생길 때 나타난다.

---

## 2. 의미
- 클라이언트가 서버에 접근하려면 인증이 필요함을 나타낸다.
- 서버는 401 응답 시 `WWW-Authenticate` 헤더를 포함하여 어떤 인증 방식이 필요한지 알려줄 수 있다.
  ```http
  HTTP/1.1 401 Unauthorized
  WWW-Authenticate: Basic realm="Access to the site"
