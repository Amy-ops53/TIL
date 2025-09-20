# Postman JSON Export / Import 로 여러 API 관리하기

## 1. 개념
Postman은 API 요청 모음(Collection)과 환경(Environment)을  
JSON 파일 형식으로 내보내기(Export)와 불러오기(Import) 할 수 있다.

- **Collection JSON**: 여러 개의 API 요청(메서드, URL, 헤더, 바디, 테스트 스크립트 포함)을 한 파일에 저장  
- **Environment JSON**: baseUrl, token 등 환경 변수를 저장

이 JSON 파일을 사용하면 다른 PC나 팀원이 동일한 API 세트를 즉시 복원할 수 있다.

---

## 2. Export (내보내기)
1. 왼쪽 컬렉션 목록에서 원하는 Collection 선택
2. `…` (More) → Export
3. 버전(2.1 권장) 선택 후 `.json` 파일로 저장  
   예: `MyProject.postman_collection.json`

환경(Environment)도 같은 방식으로 Export하면  
`MyProject.postman_environment.json` 파일을 얻을 수 있다.

---

## 3. Import (불러오기)
1. Postman 상단의 Import 클릭
2. Export된 `.json` 파일을 드래그하거나 선택
3. 컬렉션과 환경이 자동으로 생성된다

→ 한 번의 Import로 컬렉션에 포함된 모든 API 요청을 한꺼번에 가져올 수 있다.

---

## 4. 장점
| 장점 | 설명 |
|------|------|
| 대량 공유 | 여러 API 요청을 하나의 파일로 전달 |
| 버전 관리 | JSON을 Git에 저장해 변경 이력 추적 |
| 협업 편의 | 팀원은 Import만으로 동일한 테스트 환경 구성 |
| 백업 | Postman 계정 없이도 안전하게 로컬/클라우드에 보관 가능 |
