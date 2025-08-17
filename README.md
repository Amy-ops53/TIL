# study-notes

# 기술 면접 대비 Q&A (4년차 주니어 Java 개발자용)

이 문서는 Java 백엔드 개발자로 면접을 준비하면서 정리한 **주요 질문 30개**를 분야별로 정리한 것입니다.  
면접 대비 및 학습용 자료로 활용할 수 있습니다.  
> ⚠️ 모든 답변은 교재, 블로그, 공식 문서 등을 참고하여 **개인적으로 요약/정리**한 내용입니다.

---

## 📌 Java (8문항)

1. JVM의 메모리 구조(Heap, Stack, Method Area 등)에 대해 설명해주세요.  
2. Garbage Collection이 어떻게 동작하는지, Minor GC / Major GC 차이를 설명해주세요.  
3. `==` 와 `equals()`의 차이점은 무엇인가요?  
4. `HashMap` 과 `ConcurrentHashMap` 차이점은 무엇인가요?  
5. Java에서 `synchronized` 키워드를 사용하는 경우와 단점은 무엇인가요?  
6. `final`, `finally`, `finalize` 의 차이를 설명해주세요.  
7. Checked Exception과 Unchecked Exception의 차이는 무엇인가요?  
8. Java에서 `Optional` 을 쓰는 이유는 무엇인가요?  

---

## 📌 Spring & Web (8문항)

9. Spring IoC 컨테이너와 Bean의 라이프사이클을 설명해주세요.  
10. `@Component`, `@Service`, `@Repository` 차이를 설명해주세요.  
11. Spring에서 AOP를 적용하는 대표적인 사례는 무엇인가요?  
12. 트랜잭션 전파(Propagation) 옵션에는 어떤 것들이 있고, 실제로 써본 사례는 무엇인가요?  
13. `@Transactional` 어노테이션을 붙이면 내부적으로 어떤 동작이 일어나나요?  
14. Spring MVC에서 DispatcherServlet의 역할은 무엇인가요?  
15. 필터(Filter)와 인터셉터(Interceptor)의 차이는 무엇인가요?  
16. REST API 설계 시 고려해야 하는 사항(예: HTTP Status Code, idempotency 등)을 설명해주세요.  

---

## 📌 Database (6문항)

17. 인덱스(Index)의 장단점과, 인덱스를 잘못 설계했을 때의 문제점은 무엇인가요?  
18. 트랜잭션(Transaction)의 ACID 특성을 설명해주세요.  
19. 트랜잭션 격리 수준(Isolation Level)의 종류와 발생할 수 있는 문제(Dirty Read, Phantom Read 등)를 설명해주세요.  
20. DB 정규화(Normalization)의 목적과 단점은 무엇인가요?  
21. 실행 계획(Explain Plan)을 분석해본 경험이 있나요? 어떤 경우에 사용했나요?  
22. DB Deadlock이 발생하는 원인과 해결 방법은 무엇인가요?  

---

## 📌 Network & Infra (4문항)

23. HTTP와 HTTPS의 차이점을 설명해주세요.  
24. 세션(Session)과 쿠키(Cookie)의 차이를 설명해주세요.  
25. 로드 밸런서(Load Balancer)를 사용하면 어떤 장점이 있나요?  
26. REST API와 SOAP의 차이점은 무엇인가요?  

---

## 📌 실무/경험 기반 (4문항)

27. 운영 환경에서 장애(예: CPU 급등, DB 연결 오류 등)를 경험했을 때 어떻게 대응했는지 구체적으로 설명해주세요.  
28. 코드 리뷰 과정에서 자주 지적되는 부분이나, 본인이 주의하는 부분은 무엇인가요?  
29. 협업 시 Git 브랜치 전략을 어떻게 사용했는지 설명해주세요.  
30. 최근 프로젝트에서 가장 기억에 남는 성능 최적화 경험은 무엇인가요?  

---

## 📝 참고
- 이 문서는 개인 면접 대비 및 학습 목적으로 정리되었습니다.  
- 질문은 공개된 면접 자료, 블로그, 서적 등을 참고했으며, 답변은 **직접 요약/재작성**할 예정입니다.  
