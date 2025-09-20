# JDBC (Java Database Connectivity)

JDBC는 **자바 애플리케이션에서 데이터베이스와 연결하고 SQL을 실행하기 위한 표준 API**  
DB 종류(Oracle, MySQL 등)에 상관없이 동일한 방식으로 데이터베이스를 다룰 수 있게 해준다.

---

## 핵심 개념
- **DriverManager**  
  JDBC 드라이버를 통해 데이터베이스와 연결을 생성·관리
- **Connection**  
  데이터베이스와 실제 연결을 나타내며, 트랜잭션 관리와 SQL 실행 준비 담당
- **Statement / PreparedStatement**  
  SQL을 실행하기 위한 객체  
  - Statement: 단순 SQL 실행  
  - PreparedStatement: 파라미터 바인딩 및 반복 실행 최적화
- **ResultSet**  
  SELECT 쿼리 결과를 행 단위로 읽기 위한 객체

---

## 기본 동작 흐름
1. JDBC 드라이버 로드
2. DriverManager를 통해 DB 연결(Connection) 생성
3. Statement 또는 PreparedStatement로 SQL 작성·실행
4. ResultSet으로 조회 결과 처리
5. 자원 해제(Connection, Statement, ResultSet 순으로 close)

---

## 예제 (간단 흐름)
```java
Connection conn = DriverManager.getConnection(url, user, password);
PreparedStatement ps = conn.prepareStatement("SELECT * FROM users WHERE id = ?");
ps.setInt(1, 10);
ResultSet rs = ps.executeQuery();
while (rs.next()) {
    System.out.println(rs.getString("name"));
}
rs.close();
ps.close();
conn.close();
