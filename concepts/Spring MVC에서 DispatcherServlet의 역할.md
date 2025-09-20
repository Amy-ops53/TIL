# Spring MVC에서 DispatcherServlet의 역할

## 1. 개요
`DispatcherServlet`은 **Spring MVC의 핵심 프론트 컨트롤러(Front Controller)** 역할을 담당한다.  
클라이언트의 모든 요청을 가장 먼저 받아 적절한 컨트롤러로 전달하고,  
처리 결과를 뷰(View)에 연결해 응답을 반환한다.

---

## 2. 주요 흐름
1. **요청 수신**
   - 사용자가 웹 애플리케이션에 HTTP 요청을 보내면  
     `web.xml`(또는 자바 설정)에 매핑된 `DispatcherServlet`이 가장 먼저 요청을 받는다.

2. **핸들러 매핑(HandlerMapping) 조회**
   - URL, HTTP 메서드 등을 기준으로 어떤 컨트롤러(Handler)가 요청을 처리할지 결정한다.

3. **핸들러 어댑터(HandlerAdapter) 실행**
   - 결정된 컨트롤러를 실행하기 위해 적합한 어댑터를 선택한다.

4. **컨트롤러(Handler) 호출**
   - 비즈니스 로직을 수행하고 `ModelAndView` 또는 데이터(Model) 객체를 반환한다.

5. **뷰 리졸버(ViewResolver) 처리**
   - 반환된 뷰 이름을 실제 뷰(예: JSP, Thymeleaf)로 매핑한다.

6. **뷰 렌더링 및 응답 반환**
   - 모델 데이터를 뷰에 전달해 HTML 등 최종 응답을 생성하고 클라이언트에게 전달한다.

---

## 3. DispatcherServlet이 하는 일
- **Front Controller 패턴 구현**  
  모든 요청을 단일 진입점에서 처리한다.
- **요청과 응답의 중앙 집중식 관리**  
  컨트롤러, 모델, 뷰 사이의 협력을 조율한다.
- **플러그인 아키텍처 지원**  
  `HandlerMapping`, `HandlerAdapter`, `ViewResolver` 등을 손쉽게 교체·확장 가능하다.

---

## 4. 핵심 구성 요소와 관계
| 구성 요소          | 역할                                              |
|-------------------|---------------------------------------------------|
| `HandlerMapping`  | URL과 컨트롤러 매핑 결정                          |
| `HandlerAdapter`  | 선택된 컨트롤러를 실행하기 위한 어댑터             |
| `ViewResolver`    | 뷰 이름을 실제 뷰 객체(JSP, HTML 등)로 변환        |
| `ModelAndView`    | 컨트롤러 처리 결과(데이터 + 뷰 이름) 전달 객체      |

---

## 5. 정리
`DispatcherServlet`은 Spring MVC의 **중추**로서  
클라이언트 요청 → 컨트롤러 → 모델 처리 → 뷰 렌더링 → 응답 반환  
까지의 전 과정을 지휘한다.  
이를 통해 개발자는 비즈니스 로직에만 집중하고,  
요청-응답 처리 흐름은 Spring이 일관되게 관리한다.
