# 스프링 인터셉터(Interceptor)

## 1. 정의

Spring MVC에서 **클라이언트의 요청과 컨트롤러 사이**에 위치해\
요청(Request)·응답(Response)을 가로채어 **공통 로직을 수행**할 수 있는
구성 요소.

-   서블릿 필터(Filter)와 비슷하지만 **Spring MVC DispatcherServlet
    내부**에서 동작
-   컨트롤러(Handler) 실행 전후에 코드 실행 가능

------------------------------------------------------------------------

## 2. 주요 역할

-   **인증/인가**: 로그인 체크, 권한 확인
-   **공통 로깅**: 요청 URL, 처리 시간, 사용자 정보 기록
-   **데이터 전처리**: Locale 설정, 공통 모델 데이터 추가
-   **응답 후처리**: 결과 가공, 성능 측정

------------------------------------------------------------------------

## 3. 동작 흐름

요청 → **DispatcherServlet** → **Interceptor** → Controller → View →
Response

인터셉터는 세 가지 메서드를 순서대로 실행할 수 있다.

  -----------------------------------------------------------------------
  메서드                  실행 시점                      용도
  ----------------------- ------------------------------ ----------------
  `preHandle`             컨트롤러 실행 **전**           인증·권한 체크,
                                                         요청 파라미터
                                                         검증

  `postHandle`            컨트롤러 실행 **후**, View     모델 데이터
                          렌더링 **전**                  가공, 공통 속성
                                                         추가

  `afterCompletion`       View 렌더링 **후**             로깅, 리소스
                                                         정리, 예외 처리
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 4. 구현 예제

``` java
// 1) 인터셉터 클래스 작성
public class LogInterceptor implements HandlerInterceptor {
    @Override
    public boolean preHandle(HttpServletRequest request,
                             HttpServletResponse response,
                             Object handler) throws Exception {
        long start = System.currentTimeMillis();
        request.setAttribute("startTime", start);
        System.out.println(">>> 요청 시작: " + request.getRequestURI());
        return true; // true면 계속 진행, false면 요청 중단
    }

    @Override
    public void afterCompletion(HttpServletRequest request,
                                HttpServletResponse response,
                                Object handler, Exception ex) throws Exception {
        long start = (Long) request.getAttribute("startTime");
        long end = System.currentTimeMillis();
        System.out.println(">>> 요청 완료, 소요시간: " + (end - start) + "ms");
    }
}

// 2) 설정 클래스에서 등록
@Configuration
public class WebConfig implements WebMvcConfigurer {
    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(new LogInterceptor())
                .addPathPatterns("/**")      // 적용할 경로
                .excludePathPatterns("/css/**", "/js/**"); // 제외 경로
    }
}
```

------------------------------------------------------------------------

## 5. 필터(Filter)와 차이

  구분              서블릿 필터                  스프링 인터셉터
  ----------------- ---------------------------- ----------------------------
  동작 위치         DispatcherServlet **바깥**   DispatcherServlet **안쪽**
  적용 대상         모든 서블릿/리소스           Spring MVC 컨트롤러 요청
  구현 인터페이스   `javax.servlet.Filter`       `HandlerInterceptor`

------------------------------------------------------------------------

## 6. 핵심 정리

-   **요청--컨트롤러 사이의 공통 작업**을 처리하는 스프링 MVC 전용
    컴포넌트
-   주로 인증, 로깅, 성능 측정 등 **횡단 관심사(Cross-Cutting Concern)**
    를 깔끔히 분리
