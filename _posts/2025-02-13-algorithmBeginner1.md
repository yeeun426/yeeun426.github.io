---
title: "JS 알고리즘 입문 20문제"
categories: [Ureca, Algorithm]
tags: [java, ArrayList]
image:
  path: /assets/post/2025/ureca/algorithmJS.jpeg
  alt: java
published: true
---

평소 알고리즘 풀면서 깜빡깜빡했던 메서드들을 다시 한번 알고갈 수 있는 시간이라 유용했다.<br/>
첨엔 너무 많다 생각했는데 거 기초라 빨리 풀었고 다른 사람 풀이보면서 감탄하는 시간이었다.

---

### 이번 과제에서 다시 한번 짚고 넘어갈 개념

💡 repeat(n): 문자열을 n번 반복한 새로운 문자열을 반환
```js
"hi".repeat(3); // "hihihi"
```

💡 Number.isInteger(value): value가 정수인지 여부를 true 또는 false로 반환
```js
Number.isInteger(10); // true
Number.isInteger(10.5); // false
```

💡 replaceAll(search, replace): 문자열에서 search를 모두 찾아 replace로 바꾼 새로운 문자열 반환

```js
"apple apple".replaceAll("apple", "banana"); // "banana banana"
```

---

### 1. 두 수의 차
```js
function solution(num1, num2) {
    return num1-num2;
}
```

### 2. 숫자 비교하기
```js
function solution(num1, num2) {
    var answer = 0;
    return num1 == num2 ? 1 : -1 ;
}
```

### 3. 나이 출력
```js
function solution(age) {
    return 2022-age+1;
}
```

### 4. 나머지 구하기
```js
function solution(num1, num2) {
    return num1 % num2;
}
```

### 5. 몫 구하기
```js
function solution(num1, num2) {
    return parseInt(num1/num2);
}
```

### 6. 두 수의 곱
```js
function solution(num1, num2) {
    return num1 * num2;
}
```

### 7. 배열의 평균값
```js
function solution(numbers) {
    return numbers.reduce((a,b) => a+b)/numbers.length;
}
```

### 8. 각도기
```js
function solution(angle) {
    if(angle < 90) {
        return 1;
    } else if(angle == 90){
        return 2;
    } else if (angle < 180) {
        return 3;
    } else {
        return 4;
    }
}
```

### 9. 양꼬치
```js
function solution(n, k) {
    if(n >= 10) k -= parseInt(n / 10);
    let price = n * 12000 + k * 2000;
    return price;
}
```

### 10. 짝수의 합
```js
function solution(n) {
    var answer = 0;
    for(let i = 0 ; i <= n ; i+=2) {
        answer += i;
    }
    return answer;
}
```

### 11. 피자 나눠 먹기(3)
```js
function solution(slice, n) {
    return Math.ceil(n/slice);
}
```

### 12. 문자열안에 문자열
```js
function solution(str1, str2) {
   return str1.includes(str2) ? 1 : 2;
}
```

### 13. 배열 뒤집기
```js
function solution(num_list) {
    return num_list.reverse();
}
```

### 14. 최댓값 만들기(1)
```js
function solution(numbers) {
    numbers.sort((a,b) => b - a);
    return numbers[0] * numbers[1];
}
```

### 15. 편지
```js
function solution(message) {
    return message.length * 2;
}
```

### 16. 세균 증식
```js
function solution(n, t) {
    return n * 2**t;
}
```

### 17. 특정 문자 제거하기
```js
function solution(my_string, letter) {
    return my_string.split("").filter((value) => value !== letter).join("");
    // 다른 사람 풀이 (대박 코드다 !)
    // return my_string.split(letter).join('')
    // return my_string.replaceAll(letter, "");
}
```

### 18. 순서쌍의 개수
```js
function solution(n) {
    var answer = 0;
    for(let i = 1 ; i < Math.sqrt(n) ; i++) {
        if(n % i == 0) answer++;   
    }
    answer *= 2;
    return Number.isInteger(Math.sqrt(n)) ? ++answer : answer;
}
```

### 19. 문자 반복 출력하기
```js
function solution(my_string, n) {
    var answer = '';
    for(let str of my_string) {
        answer += str.repeat(n);
    }
    return answer;
}
```

### 20. 배열 자르기
```js
function solution(numbers, num1, num2) {
    return numbers.slice(num1, num2+1);
}
```