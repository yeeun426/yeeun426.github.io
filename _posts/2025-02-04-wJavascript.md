---
title: "Javascript 간단 개념 모음"
categories: [Frontend, JS]
tags: [alert, prompt, innerHTML, innerText, AJAX, spread 연산자 ]
image:
  path: /assets/post/2025/javascript/JS.png
  alt: javascript
published: true
---

내일 시험을 앞두고 강사님이 추려주신 범위를 간략히 정리해보았다.

---

## 🔹 alert vs. prompt
alert(message): 메시지를 표시하는 알림 창을 띄움. 확인 버튼만 존재.
```js
alert("경고! 잘못된 입력입니다.");
```
prompt(message, default): 사용자의 입력을 받을 수 있는 창을 띄움.
```js
let name = prompt("이름을 입력하세요", "홍길동");
alert(`안녕하세요, ${name}님!`);
```

---

## 🔹 innerHTML vs. innerText
innerHTML: 요소의 HTML 내용을 변경. HTML 코드로 변환되어 렌더링됨
```js
document.getElementById("demo").innerHTML = "<b>굵은 텍스트</b>";
```

innerText: 요소의 텍스트만 변경. 텍스트 그대로 표시됨 (HTML 코드 해석 안 함)
```js
document.getElementById("demo").innerText = "<b>굵은 텍스트</b>";
```
✅ innerText는 보이지 않는 스타일(display: none;)의 요소 내용을 가져오지 않음.

```html
<div id="demo">Hello <b>World</b>!</div>
<button onclick="changeText()">변경하기</button>

<script>
  function changeText() {
    let el = document.getElementById("demo");

    console.log("innerHTML:", el.innerHTML); // "Hello <b>World</b>!"
    console.log("innerText:", el.innerText); // "Hello World!"

    el.innerHTML = "<i>안녕하세요!</i>"; // `<i>` 태그 적용됨
    el.innerText = "<i>안녕하세요!</i>"; // "<i>안녕하세요!</i>" 그대로 표시됨
  }
</script>
```
---

## 🔹 ES6 spread 연산자 (...)
배열이나 객체를 펼쳐서 개별 요소로 변환하는 연산자
```js
let arr1 = [1, 2, 3];
let arr2 = [...arr1, 4, 5]; // [1, 2, 3, 4, 5]

let obj1 = { a: 1, b: 2 };
let obj2 = { ...obj1, c: 3 }; // { a: 1, b: 2, c: 3 }
```

---

## 🔹 배열의 메소드와 속성
### method

|method|역할|
|---|---|
|.push() | 배열 끝에 요소 추가|
|.pop() | 배열 끝 요소 제거|
|.shift() | 배열 첫 요소 제거|
|.unshift() | 배열 앞에 요소 추가|
|.slice(start, end) | 배열 일부 복사 (원본 유지)|
|.splice(start, deleteCount, item1, item2, ...) | 배열 요소 삭제 또는 추가|
|.map(callback) | 배열 요소 변환하여 새 배열 반환|
|.filter(callback) | 조건에 맞는 요소만 반환|
|.reduce(callback, initialValue) | 누적 연산 수행|
|.forEach(callback) | 요소 순회|

---

### 속성
✅ length : 배열 길이
```js
let arr = [10, 20, 30];
console.log(arr.length); // 3
```

✅ Array.isArray() :배열 여부 확인
```js
console.log(Array.isArray([1, 2, 3])); // true
console.log(Array.isArray({ a: 1, b: 2 })); // false
```

---

## 🔹 BOM(Browser Object Model)과 DOM(Document Object Model)
### BOM (Browser Object Model)
브라우저 창 관련 객체

- window : 최상위 객체
- navigator : 브라우저 정보
- screen : 화면 크기 정보
- location : 현재 URL 정보
- history : 방문 기록 관리

### DOM (Document Object Model)
HTML 문서를 객체로 표현

- document.getElementById(id) : 특정 ID 요소 선택
- document.querySelector(selector) : CSS 선택자로 요소 선택
- document.createElement(tag) : 새 요소 생성
- document.appendChild(node) : 요소 추가
- document.removeChild(node) : 요소 제거

---

## 🔹 증가/감소, 비교 연산자 사용법
### 증가/감소 연산자
```js
let a = 5;
console.log(a++); // 5 (후위 증가, 출력 후 증가)
console.log(++a); // 7 (전위 증가, 증가 후 출력)
console.log(a--); // 7 (후위 감소)
console.log(--a); // 5 (전위 감소)
```

### 비교 연산자
- == : 값만 비교 (타입 변환 발생)
- === : 값과 타입 모두 비교
- != : 값만 다르면 true
- !== : 값 또는 타입이 다르면 true
- < , >,  >= , <= : 크기 비교

```js
console.log(5 == "5");  // true (타입 변환됨)
console.log(5 === "5"); // false (타입 다름)
console.log(10 > 5);    // true
```

---

## 🔹 AJAX (Asynchronous JavaScript and XML)
- 서버와 비동기적으로 데이터를 교환하는 기술.
- fetch() 사용.

```js
fetch("서버 url")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

---

## 🔹 타입스크립트 기본 타입 & interface
기본 타입
```ts
let isDone: boolean = false;
let age: number = 25;
let userName: string = "Alice";
let numbers: number[] = [1, 2, 3];
let tuple: [string, number] = ["hello", 10]; // 튜플
```
인터페이스 (interface)

```ts
interface Person {
  name: string;
  age: number;
  isStudent?: boolean; // 선택적 속성
}

let user: Person = { name: "Bob", age: 30 };
```