# Git Label 요약

---

## 1. 개요
- **Git Label**은 주로 **GitHub, GitLab, Bitbucket** 등 협업 플랫폼에서 **이슈(Issue)와 Pull Request(PR)를 분류/관리**하기 위해 사용하는 태그(tag) 개념이다.
- Git 자체의 로컬 명령어에는 label 기능이 없으며, **이슈 트래킹 시스템에서 제공하는 메타데이터**라고 이해하면 된다.

---

## 2. 목적
- 작업의 성격, 우선순위, 상태를 한눈에 구분할 수 있게 함.
- 협업 시 팀원 간의 소통을 원활하게 함.
- 프로젝트 관리 도구(Jira, Notion 등)와 연계해 워크플로우를 체계화.

---

## 3. 자주 사용하는 Label 예시
1. **기능 개발(Feature) 관련**
   - `feat`: 새로운 기능 추가
   - `enhancement`: 기존 기능 개선

2. **버그 수정(Bugfix) 관련**
   - `fix`: 버그 수정
   - `bug`: 버그 리포트

3. **테스트/배포 관련**
   - `test`: 테스트 코드 관련
   - `ci/cd`: 빌드/배포 파이프라인 관련

4. **문서/기타**
   - `docs`: 문서 작업
   - `chore`: 사소한 작업(빌드, 설정 변경 등)
   - `refactor`: 리팩토링

5. **우선순위/상태**
   - `priority: high`, `priority: low`
   - `in progress`, `ready for review`, `done`

---

## 4. 사용 방법
- GitHub/GitLab Issue 또는 Pull Request 화면에서 Label을 지정.
- Label 색상과 이름을 커스터마이징 가능.
- Label 조합으로 이슈를 필터링하거나 대시보드에서 상태 관리 가능.

---

## 5. 요약
- **Git Label**은 Git 명령어가 아닌 협업 플랫폼의 **이슈/PR 관리 기능**이다.  
- 목적: 이슈/PR의 성격, 우선순위, 진행 상태를 **쉽게 구분**하기 위함.  
- `feat`, `fix`, `docs`, `refactor`, `test`, `chore` 등이 가장 흔히 사용된다.  
- 잘 정리된 Label은 프로젝트 가독성과 협업 효율을 크게 높인다.
