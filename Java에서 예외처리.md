# Java 예외 처리 (Exception Handling)

자바의 예외 처리는 프로그램 실행 중 발생할 수 있는 오류 상황을 안전하게 처리해  
프로그램이 비정상 종료되지 않도록 하는 메커니즘이다.

---

## 1. 예외(Exception)와 에러(Error)

| 구분   | 설명 | 예시 |
|--------|------|-----|
| **에러(Error)** | JVM 내부에서 발생, 복구 불가 | OutOfMemoryError, StackOverflowError |
| **예외(Exception)** | 코드에서 잡아서 처리 가능 | IOException, NullPointerException |

---

## 2. 체크 예외 vs 언체크 예외

| 종류 | 특징 | 예시 |
|------|------|-----|
| **체크 예외(Checked Exception)** | 컴파일 시점에 반드시 처리해야 함 (`try-catch` 또는 `throws`) | IOException, SQLException |
| **언체크 예외(Unchecked Exception)** | RuntimeException 하위, 명시적 처리 강제 없음 | NullPointerException, IllegalArgumentException |
