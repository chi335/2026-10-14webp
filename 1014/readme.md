# 📘 Chapter 07. 자바스크립트 코어 객체와 배열

> **명품 웹 프로그래밍 Chapter 07** 학습 내용을 바탕으로 정리한 문서입니다.  
> 자바스크립트의 객체 개념, 배열, 그리고 주요 코어 객체(`Array`, `Date`, `String`, `Math`)의 특징 및 활용법을 다룹니다.

---

## 📑 목차
1. [자바스크립트 객체 개요](#1-자바스크립트-객체-개요)
2. [자바스크립트 배열 (Array)](#2-자바스크립트-배열-array)
3. [Date 객체](#3-date-객체)
4. [String 객체](#4-string-객체)
5. [Math 객체](#5-math-객체)
6. [사용자 정의 객체](#6-사용자-정의-객체)

---

## 1. 자바스크립트 객체 개요

### 💡 객체(Object)란?
- **프로퍼티(Property)**: 객체의 상태 또는 속성을 나타내는 값 (변수)
- **메소드(Method)**: 객체가 수행할 수 있는 동작 (함수)

### 📌 객체 프로퍼티 및 메소드 접근
```javascript
// 프로퍼티 값 읽기/변경
let name = account.owner; // 값 읽기
account.balance = 50000;  // 값 변경

// 메소드 호출
account.deposit(10000);
```

---

## 2. 자바스크립트 배열 (Array)

### 💡 배열 생성 방법
자바스크립트에서는 두 가지 방법으로 배열을 생성할 수 있습니다.

1. **대괄호 `[]` 리터럴 이용 (권장)**
   ```javascript
   let cities = ["Seoul", "New York", "Paris"];
   let numbers = [1, 2, 3, 4, 5];
   ```
2. **`Array` 객체 생성자 이용**
   ```javascript
   let arr = new Array(5); // 크기가 5인 빈 배열 생성
   let days = new Array("월", "화", "수");
   ```

### 📌 자바스크립트 배열의 특징
- 배열은 내부적으로 **`Array` 객체**로 다루어집니다.
- **다양한 데이터 타입 혼용 가능**: 한 배열 안에 숫자, 문자열, 객체, 함수 등을 섞어서 저장할 수 있습니다.
- 배열의 크기는 동적으로 조절됩니다.

### 🛠️ Array 객체의 주요 메소드

| 메소드 | 설명 | 원본 변경 여부 |
| :--- | :--- | :---: |
| `concat(arr)` | 두 개 이상의 배열을 결합하여 새 배열 반환 | X |
| `join([separator])` | 배열의 모든 요소를 하나의 문자열로 연결 | X |
| `reverse()` | 배열의 요소 순서를 반대로 뒤집음 | **O** |
| `slice(start, end)` | 배열의 일부를 추출하여 새 배열 생성 ($start \le index < end$) | X |
| `sort()` | 배열 요소를 정렬 | **O** |
| `toString()` | 배열 원소를 쉼표(`,`)로 연결한 문자열 반환 | X |

---

## 3. Date 객체

날짜와 시간 정보를 취급하기 위한 코어 객체입니다.

### 💡 생성 및 활용 예시
```javascript
// 현재 날짜 및 시간
let now = new Date();

// 특정 날짜 지정 (년, 월-1, 일) -> 월은 0부터 시작하므로 3월은 2 입력
let startDay = new Date(2024, 2, 1); 
```

### 🛠️ Date 객체의 주요 메소드
- `getFullYear()` : 4자리 연도 반환
- `getMonth()` : 월 반환 (**0~11**의 값 반환, 실제 월을 구하려면 `+ 1` 필요)
- `getDate()` : 일 반환 (1~31)
- `getDay()` : 요일 반환 (0: 일요일 ~ 6: 토요일)
- `getHours()`, `getMinutes()`, `getSeconds()` : 시, 분, 초 반환
- `toLocaleString()` : 현지 시간 형태의 문자열로 변환
- `toUTCString()` : UTC 시간 형태의 문자열로 변환

---

## 4. String 객체

문자열을 다루기 위한 객체입니다.

### 📌 String 객체의 특징
- `length` 프로퍼티는 문자열의 길이를 나타내며 **읽기 전용(Read-Only)** 입니다.
- 배열처럼 인덱스 표기법(`str[0]`)을 사용하여 각 문자에 접근할 수 있습니다.

### 🛠️ String 객체의 주요 메소드

```javascript
let str = "Boys and Girls";

str.charAt(0);           // "B" (해당 인덱스의 문자 반환)
str.indexOf("and");      // 5 (문자열 검색, 없을 경우 -1 반환)
str.slice(5, 8);         // "and" (문자열 일부 추출)
str.toUpperCase();       // "BOYS AND GIRLS" (대문자로 변환)
str.replace("and", "or");// "Boys or Girls" (문자열 치환)
"  hello  ".trim();      // "hello" (양쪽 공백 제거)
str.split(" ");          // ["Boys", "and", "Girls"] (구분자로 분리하여 배열 생성)
```

---

## 5. Math 객체

수학 계산을 위한 프로퍼티와 메소드를 제공합니다.

### 📌 Math 객체의 특징
- `new Math()`로 인스턴스를 생성하지 않고, 클래스명/객체명으로 직접 사용합니다. (**Static 형태**)

### 🛠️ 주요 프로퍼티 및 메소드
- **`Math.PI`**: 원주율 값 ($\pi \approx 3.14159$)
- **`Math.random()`**: $0$ 이상 $1$ 미만의 난수(실수) 발생
- **`Math.floor(n)`**: 소수점 이하 내림 (정수 변환)
- **`Math.ceil(n)`**: 소수점 이하 올림
- **`Math.round(n)`**: 소수점 이하 반올림
- **`Math.sqrt(n)`**: $n$의 제곱근 계산

### 🎲 난수 활용 예시 (0~99 사이의 정수 생성)
```javascript
let randomNum = Math.floor(Math.random() * 100);
```

---

## 6. 사용자 정의 객체

개발자가 필요에 따라 직접 새로운 형태의 객체를 정의하여 사용할 수 있습니다.

1. **`Object` 객체 이용**
   ```javascript
   let user = new Object();
   user.name = "홍길동";
   user.age = 20;
   ```
2. **리터럴 표기법 이용**
   ```javascript
   let user = {
       name: "홍길동",
       age: 20
   };
   ```
