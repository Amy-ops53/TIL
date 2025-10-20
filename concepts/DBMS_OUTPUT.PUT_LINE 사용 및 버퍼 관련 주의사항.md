# DBMS_OUTPUT.PUT_LINE 사용 및 버퍼 관련 주의사항

## 1. 개요
`DBMS_OUTPUT.PUT_LINE`은 Oracle PL/SQL에서 **프로시저 실행 중 로그나 메시지를 출력할 때** 사용하는 내장 패키지다.  
주로 **디버깅**이나 **로직 확인용 출력문**으로 사용된다.

```sql
BEGIN
    DBMS_OUTPUT.PUT_LINE('처리 시작');
    UPDATE user_table SET status = 'DONE';
    DBMS_OUTPUT.PUT_LINE('처리 완료');
END;
```

위 예시는 PL/SQL 실행 시 콘솔(예: SQL Developer, DataGrip 등)에 메시지를 출력한다.

---

## 2. 작동 방식
- DBMS_OUTPUT은 실제 화면에 바로 찍히지 않는다.
- 내부적으로 **버퍼(buffer)** 에 문자열을 저장하고, 실행이 끝나면 클라이언트가 이 버퍼를 읽어 출력한다.
- 즉, `DBMS_OUTPUT.PUT_LINE`은 **출력 버퍼에 문자열을 쌓는 역할**을 한다.

---

## 3. 버퍼 제한 및 문제점
| 항목 | 설명 |
|------|------|
| 기본 버퍼 크기 | 20,000 byte (버전별로 다를 수 있음) |
| 최대 버퍼 크기 | 1,000,000 byte (1MB) |
| 초과 시 현상 | ORA-20000: ORU-10027: buffer overflow, limit of 1000000 bytes reached |
| 발생 원인 | DBMS_OUTPUT.PUT_LINE을 과도하게 사용하여 버퍼를 초과할 때 |

### 예시
```sql
BEGIN
    FOR i IN 1..200000 LOOP
        DBMS_OUTPUT.PUT_LINE('로그 출력 ' || i);
    END LOOP;
END;
/
-- ORA-20000: ORU-10027: buffer overflow
```

---

## 4. 성능 및 운영상 주의사항
1. **버퍼 메모리 사용 증가**
   - `PUT_LINE`을 많이 호출하면 버퍼가 쌓여 **PGA 메모리 사용량 증가**  
   - 장시간 실행 시 불필요한 메모리 점유 가능

2. **성능 저하**
   - 수천~수만 번 로그를 찍으면 PL/SQL 실행 속도에 영향 발생  
   - 실제 트랜잭션보다 로그 처리 비용이 커질 수 있음

3. **운영 환경에서는 비활성화 권장**
   - `DBMS_OUTPUT`은 개발/테스트용  
   - 운영 서버에서는 **로그 테이블 삽입**이나 **파일 로깅** 방식 사용 권장

---

## 5. 대체 방법
| 목적 | 권장 방식 |
|------|------------|
| 디버깅 | DBMS_OUTPUT.PUT_LINE |
| 운영 로그 저장 | LOG 테이블에 INSERT |
| 에러 추적 | EXCEPTION 블록 + 로그 테이블 |
| 대량 로그 | 임시 테이블 또는 파일 로깅 (UTL_FILE 등) |

---

## 6. 정리
| 항목 | 요약 |
|------|------|
| DBMS_OUTPUT.PUT_LINE 역할 | 콘솔용 출력 버퍼에 로그 저장 |
| 버퍼 제한 | 최대 1MB |
| 과도한 사용 시 | ORU-10027 에러, 메모리 낭비, 성능 저하 |
| 운영 시 권장 방법 | DBMS_OUTPUT 최소화, 로그 테이블 사용 |

---

## 참고
- Oracle 공식 문서: [DBMS_OUTPUT Package (Oracle Docs)](https://docs.oracle.com/en/database/oracle/oracle-database/)
- 관련 에러: ORA-20000, ORU-10027
