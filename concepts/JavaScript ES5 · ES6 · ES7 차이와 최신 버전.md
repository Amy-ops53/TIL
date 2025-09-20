# JavaScript ES5 · ES6 · ES7 차이와 최신 버전

## 1. ECMAScript 개요
- **ECMAScript(ES)**: JavaScript 표준 사양  
- **버전 명칭**  
  - ES1~ES5: 숫자 표기  
  - ES6 이후: 발표 연도 표기 (예: ES2015, ES2016)

---

## 2. ES5 (2009)
**주요 특징**
- `strict mode` (`"use strict"`)
- JSON 표준 내장(`JSON.parse`, `JSON.stringify`)
- `Array` 메서드: `forEach`, `map`, `filter`, `reduce`, `every`, `some`
- `Object` 메서드: `Object.create`, `Object.defineProperty`
- `Function.prototype.bind`
- 표준화된 `Date`·`String` 메서드 확장

---

## 3. ES6 / ES2015
**가장 큰 전환점**

| 영역 | 추가 기능 |
|------|-----------|
| 변수 | `let`, `const` |
| 함수 | Arrow Function `()=>{}` |
| 클래스 | `class`, `constructor`, `extends` |
| 모듈 | `import`, `export` |
| 템플릿 문자열 | `` `Hello ${name}` `` |
| 구조 분해 | `const {a,b} = obj`, `const [x,y] = arr` |
| Promise | 비동기 처리 |
| 기타 | `Set`, `Map`, `Symbol`, Default parameter, Rest/Spread `...` |

---

## 4. ES7 / ES2016
**소규모 개선**

| 추가 기능 | 설명 |
|----------|-----|
| `Array.prototype.includes` | 값 존재 여부 확인 |
| 지수 연산자 `**` | `2 ** 3 // 8` |

---

## 5. 이후 주요 버전 하이라이트
- **ES2017**: `async/await`, `Object.values/entries`
- **ES2018**: Rest/Spread for objects, `Promise.finally`
- **ES2019**: `Array.flat`, `Array.flatMap`, `Object.fromEntries`
- **ES2020**: Optional Chaining `?.`, Nullish Coalescing `??`, BigInt
- **ES2021**: Logical assignment `&&=`, `||=`, `??=`
- **ES2022**: Top-level `await`, Class static initialization blocks
- **ES2023**: Array `findLast`, `findLastIndex`, Hashbang Grammar
- **ES2024**: toSorted / toSpliced 등 새로운 Array 메서드

---

## 6. 현재 최신 버전
- **ECMAScript 2024 (ES15)** 가 최신 정식 사양  
- TC39(표준 위원회)는 매년 6월 새로운 버전을 발표  
- 브라우저는 대부분 최신 스펙을 점진적으로 지원
