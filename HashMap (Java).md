# HashMap (Java)

Java에서 가장 많이 사용하는 **Key-Value(키-값)** 기반 자료구조.  
키를 이용해 값을 빠르게 검색할 수 있으며, 내부적으로 **해시 함수**를 사용한다.

---

## 특징
- **키는 중복 불가**, 값은 중복 가능  
- **null 허용**: 키는 하나만, 값은 여러 개 가능  
- **순서 보장 없음** (순서 필요 → `LinkedHashMap`)  
- **스레드 안전하지 않음** (멀티스레드 환경 → `ConcurrentHashMap`)  
- 평균 시간 복잡도:  
  - 삽입(`put`) : O(1)  
  - 검색(`get`) : O(1)  
  - 삭제(`remove`) : O(1)  

---

## 주요 메서드
- `put(key, value)` : 데이터 추가  
- `get(key)` : 값 조회  
- `remove(key)` : 삭제  
- `containsKey(key)` / `containsValue(value)` : 존재 여부 확인  
- `keySet()` : 모든 키 반환  
- `values()` : 모든 값 반환  
- `entrySet()` : 모든 키-값 쌍 반환  
        }
    }
}
