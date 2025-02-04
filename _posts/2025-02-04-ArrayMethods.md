---
title: "[Day7] Array Methods"
categories: [Ureca, Javascript]
tags: [forEach, map, filter, reduce, Map]
image:
  path: /assets/post/2025/ureca/array.webp
  alt: ArrayMethods
published: true
---

오늘 수업에서는 w3school로 array와 타입스크립트를 훑어보았다. 
기존에는 수업을 들으며 블로그 쓸 부분만 간단히 메모해뒀는데 수업끝나고 스터디 노트 쓰는게 너무 오래걸려서 (어제는 새벽 3시에 잤음) 이제는 바로바로 정리하면서 들었다. 따라가지 못하고 받아적고만 있을까봐 걱정했는데 훨씬 수월했다. 

# JS Array Iteration
## forEach()
- 배열의 각 요소에 한번씩 주어진 함수를 실행한다.
- return 없다 ! (undefined)
- 원본 배열을 변경하지 않는다. 
 
### param
1. currentValue (배열 원소의 값)
2. index (현재 요소의 인덱스)
3. array (현재 배열)
```js
arr.forEach(num => { mulArr.push(num * 3); });
```

## map()
- 배열 내의 모든 요소에 대해 주어진 콜백을 호출한 결과를 모아 새로운 배열을 반환
- 원본 배열을 변경하지 않는다.    
-> 처리된 결과 자체를 return 받는다.
<br/>
💡 성능면에서는 map이 forEach보다 빠르고 유리하다.💡

### param
1. currentValue (배열 원소의 값)
2. index (현재 요소의 인덱스)
3. array (현재 배열)

```js
const numbers1 = [45, 4, 9, 16, 25];
const numbers2 = numbers1.map(myFunction);
// numbers2를 콘솔로 찍으면 [90, 8, 18, 32, 50]
document.getElementById("demo").innerHTML = numbers2;
function myFunction(value, index, array) {
  return value * 2;
}
```

## filter()
- 주어진 함수의 결과값이 true인 요소로 새로운 배열을 반환
- 원본이 바뀌지 않음. 
- return 값 있음.

### param
1. currentValue (배열 원소의 값)
2. index (현재 요소의 인덱스)
3. array (현재 배열)

```js
const numbers = [45, 4, 9, 16, 25];
const numFilter = numbers.filter((value, index, array) => {
  return value.length > 5;
})
```

## reduce()
: 각 배열 요소에서 함수를 실행하여eks 단 하나의 결과값을 반환
```js
const numbers = [45, 4, 9, 16, 25];
let sum = numbers.reduce(myFunction); // 99

function myFunction(acc, cur) {
  return acc + cur;
}
```
* reduceRight() : 배열의 오른쪽에서 왼쪽으로 작동하고 싶을 때 사용

## splice()
: 배열의 특정 위치에 요소를 추가하거나 삭제
splice(index, 제거할 요소 개수, 배열에 추가될 요소)
```js
var arr = [ 1, 2, 3, 4, 5, 6, 7 ];
arr.splice( 3, 2 );
console.log( arr ); 
// [ 1, 2, 3, 6, 7 ]   3번째 인덱스에서부터 2개 제거

var arr = [ 1, 2, 3, 4, 5, 6, 7 ];
arr.splice( 2, 1, "a", "b");
console.log( arr ); 
// [ 1, 2, "a", "b", 4, 5, 6, 7 ] 2번째 인덱스에서 1개 제거 후 "a"와 "b"를 추가
```
<img src="/assets/post/2025/ureca/array.webp" alt='' width=1300px>

|method|역할|
|---|---|
|pop|배열 마지막 요소 삭제|
|shift|배열 맨 앞 요소 삭제|
|push|배열 뒷 부분에 삽입|
|unshift|배열 앞 부분에 삽입|
|slice(startIndex, endIndex)|배열의 startIndex부터 endIndex까지에 대한 새로운 배열 반환|
|concat|다수의 배열을 합치고 병합된 배열의 사본을 반환|
|every|배열의 모든 요소가 제공한 함수를 통과하는지 테스트|
|some|지정된 함수의 결과가 true일 때까지 배열의 각 원소를 반복|

---

# Map Object
- Map은 key-value 형태의 자료형으로 이루어진 컬렉션
- js의 object와는 달리, key가 반드시 문자열이 아니어도 됨.

```js
// Create a Map
const fruits = new Map([
  ["apples", 500],
  ["bananas", 300],
  ["oranges", 200]
]);

let text = "";
fruits.forEach (function(value, key) {
  text += key + ' = ' + value + "<br>"
})

document.getElementById("demo").innerHTML = text;
```
 
## Map의 기본 동작

|동작|역할|
|---|---|
|set(key,value)|키-값 쌍을 추가 -> 중복 값은 대체|
|get(key)|키에 해당하는 값 반환 -> 존재하지 않으면 undefined|
|has(key)|Map객체가 해당 키를 갖고 있는 지 확인. boolean|
|delete(key)|주어진 키와 값을 삭제|
|clear()|Map객체의 모든 요소를 제거|
|size|Map객체의 요소 크기 반환 -> 메서드 아님 !|

## JS Map Iteration
### entries()
Map 객체 내 모든 키-값 쌍(key-value pair)을 각각 순회

```js
// Create a Map
const fruits = new Map([
  ["apples", 500],
  ["bananas", 300],
  ["oranges", 200]
]);

let text = "";
for (const x of fruits.entries()) {
  text += x + "<br>";
}
document.getElementById("demo").innerHTML = text;
```

🔹 그럼 entries()를 왜 사용할까? 에 대한 의문 🔹 
<img src="/assets/post/2025/ureca/array2.png" alt='' width=1300px>
> 정리를 하다보니 Map 그자체로 사용해도 key-value가 출력이 되는데 굳이 Map.entries()를 사용해야되는 이유가 궁금하다.

✅ 강사님이 보여주신 Map의 entries()와 구조분해할당의 비교
<img src="/assets/post/2025/ureca/array1.png" alt='' width=1300px>

✅ chatGpt에게 물어본 결론 
- Map 자체를 순회하면 기본적으로 [key, value] 배열을 반환하므로 entries()를 생략해도 됨.
- 하지만 가독성, 명확한 의도, 다른 메서드(keys(), values())와의 일관성을 고려해서 entries()를 사용하는 것이 좋을 때도 있음.
- entries()를 반드시 써야 하는 건 아니지만, 더 명확하고 일관된 코드 작성을 위해 사용할 수 있음!
<br/>
내일 보조 강사님께 질문하고 추가 결론을 작성해야겠다

### keys()
Map 객체 내 모든 키(key)를 반환

```js
for (const x of fruits.keys()) {
  text += x; 
  // apples 
  // bananas 
  // oranges
}
```

### values()
Map 객체 내 모든 값(value)을 반환.

```js
for (const x of fruits.values()) {
  text += x; 
  // 500 
  // 300 
  // 200
}
```
---

### Reference
이 포스트는 아래 게시글의 정보 및 이미지가 사용되었습니다.
1. [w3schools](https://www.w3schools.com/js/)

---

## END
