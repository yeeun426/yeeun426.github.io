---
title: "JS 알고리즘 입문 40문제"
categories: [Ureca, Algorithm]
tags: [javascript, algorithm]
image:
  path: /assets/post/2025/ureca/algorithmJS.jpeg
  alt: JS
published: true
---

### 1. 두 수의 나눗셈
```js
function solution(num1, num2) {
    return parseInt(num1 / num2 * 1000);
}
```

### 2. 짝수 홀수 개수
```js
function solution(num_list) {
    var answer = [0,0];
    for(let num of num_list) {
        if(num % 2 == 0) {
            answer[0]++
        } else {
            answer[1]++
        }
    }
    return answer;
}
```

### 3. 두수의 합
```js
function solution(num1, num2) {
    return num1+num2;
}
```

### 4. 문자열 뒤집기
```js
function solution(my_string) {
    return my_string.split("").reverse().join("");
}
```

### 5. 점의 위치 구하기
```js
function solution(dot) {
    var answer = 0;
    const [x, y] = dot;
    
    if(x > 0 && y > 0) {
        return 1;
    } else if ( x < 0 && y > 0) {
        return 2;
    } else if (x < 0 && y < 0) {
        return 3;
    } else {
        return 4;
    }
}
```

### 6. 아이스 아메리카노
```js
function solution(money) {
    const coffePrice = 5500;
    return [parseInt(money/coffePrice), money % coffePrice];
}
```

### 7. 삼각형의 완성조건(1)
```js
function solution(sides) {
    var answer = 0;
    sides.sort((a,b) => a-b);
    
    if(sides[0] + sides[1] > sides[2]) return 1
    return 2;
}
```

### 8. n의 배수 고르기
```js
function solution(n, numlist) {
    var answer = [];
    for(let num of numlist) {
        if(num % n == 0) answer.push(num);
    }
    return answer;
}
```

### 9. 배열의 유사도
```js
function solution(s1, s2) {
    var answer = 0;
    
    for(let i = 0 ; i < s1.length ; i++) {
        for(let j = 0 ; j < s2.length ; j++) {
            
            if(s1[i] == s2[j]) {
                answer++;
            }
        }
    }
    return answer;
}
```

### 10. 머쓱이보다 키 큰 사람
```js
function solution(array, height) {
    array.sort((a,b) => a-b);
    
    for(let i = 0 ; i < array.length ; i++) {
        if(array[i] > height) return array.length - i;
    }
    
    return 0;
}

// 다른 사람 풀이 (filter 사용 !)
function solution(array, height) {
    var answer = array.filter(item => item > height);
    return answer.length;
}
```

### 11. 피자 나눠먹기 (1)
```js
function solution(n) {
    return Math.ceil(n / 7);
}
```

### 12. 자릿수 더하기
```js
function solution(n) {
    return n.toString().split("").map(Number).reduce((a,b) => a+b);
}
```

### 13. 모음 제거
```js
function solution(my_string) {
    var answer = '';
    const alphabet = ["a", "e", "i", "o", "u"];
    
    answer = my_string.split("").filter((value) => !alphabet.includes(value)).join("")
    return answer;
}

// 다른 사람 풀이 (정규표현식)
function solution(my_string) {
    return my_string.replace(/[aeiou]/g, '');
}
```

### 14. 배열 원소의 길이
```js
function solution(strlist) {
    var answer = [];
    for(let i of strlist) {
        answer.push(i.length);
    }
    return answer;
}
// 다른 사람 풀이 (map은 return값 존재)
function solution(strlist) {
    return strlist.map((el) => el.length)
}
```

### 15. 중복된 숫자의 개수
```js
function solution(array, n) {
    return array.filter((el) => el == n).length;
}
```

### 16. 배열 두 배 만들기
```js
function solution(numbers) {
    return numbers.map((el) => el * 2);
}
```

### 17. 중앙값 구하기
```js
function solution(array) {
    return array.sort((a,b) => a - b)[parseInt(array.length / 2)];
}
```

### 18. 짝수는 싫어요
```js
function solution(n) {
    var answer = [];
    for(let i = 1 ; i <= n ; i+=2) {
        answer.push(i)
    }
    return answer;
}
```

### 19. 옷가게 할인 받기
```js
function solution(price) {
    if(price >= 500000) return parseInt(price * 0.8);
    if(price >= 300000) return parseInt(price * 0.9);
    if(price >= 100000) return parseInt(price * 0.95);
    
    return price;
}
```

### 20. 직삼각형 출력하기
```js
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

let input = [];

rl.on('line', function (line) {
    input = line.split(' ');
}).on('close', function () {
    n = Number(input[0]);
    
    for(let i = 1 ; i < n+1 ; i++) {
        console.log("*".repeat(i))
    }
});
```

### 21. 개미군단
```js
function solution(hp) {
    var answer = 0;
    answer += parseInt(hp / 5);
    hp = hp % 5;
    answer += parseInt(hp / 3);
    hp = hp % 3;
    answer += hp;
    return answer;
}
```

### 22. 가위 바위 보
```js
function solution(rsp) {
    const winner = {"2" : "0", "0" : "5", "5":"2"};
    return rsp.split("").map((el) => winner[el]).join("");
}
```

### 23. 숨어있는 숫자의 덧셈 (1)
```js
function solution(my_string) {
    var answer = 0;
    for(let str of my_string.split("")) {
        let number = Number(str);
        if(number > 0) answer += number;
    }
    return answer;
}

// 다른 사람 풀이
function solution(my_string) {
    return [...my_string].reduce((acc,cur)=> Number(cur) ? +acc + +cur : acc, 0)
}
```

### 24. 최댓값 만들기 (2) 
```js
function solution(numbers) {
    numbers.sort((a,b) => a-b);
    return Math.max(numbers[0] * numbers[1] , numbers[numbers.length - 1] * numbers[numbers.length - 2]);
}
```

### 25. 대문자와 소문자
```js
function solution(my_string) {
    let result = "";    
    for(let str of my_string){
        if(str.charCodeAt() >= 97 ) result += String.fromCharCode(str.charCodeAt() - 32);
        else result += String.fromCharCode(str.charCodeAt() + 32);
    }
    return result
}
```

### 26. 인덱스 바꾸기
```js
function solution(my_string, num1, num2) {
    var answer = my_string.split("");
    answer[num1] = my_string[num2];                
    answer[num2] = my_string[num1];
    return answer.join("");
}
```

### 27. 약수 구하기
```js
function solution(n) {
    var answer = []; 
    for(let i = 1 ; i <= n ; i++) {
        if(n % i == 0) answer.push(i)
    }
    return answer;
}
```

### 28. 가장 큰 수 찾기
```js
function solution(array) {
    return [Math.max(...array), array.indexOf(Math.max(...array))];
}
```

### 29. 문자열 정렬하기 (1)
```js
function solution(my_string) {
    return my_string.split("").filter((value) => !isNaN(value)).map(Number).sort((a,b) => a-b);
}
```

### 30. 암호 해독
```js
function solution(cipher, code) {
    var answer = '';
    let idx;
    
    for(let i = 1 ; i <= cipher.length / code ; i++) {
        idx = code * i;
        answer += cipher[idx-1];
    }
    return answer;
}
```

### 31. 주사위 개수
```js
function solution(box, n) {
    return parseInt(box[0] / n) * parseInt(box[1] / n) * parseInt(box[2] / n);
}
```

### 32. 문자열 정렬하기 (2)
```js
function solution(my_string) {
    return my_string.toLowerCase().split("").sort().join("");
}
```

### 33. 제곱수 판별하기
```js
function solution(n) {
    return Math.sqrt(n) % 1 ? 2 : 1;
}
```

### 34. 피자 나눠먹기 (2)
```js
function solution(n) {
    var answer = 0;
    let i = 1;
    while(true) {
        let pizza = 6 * i;
        answer++;
        if(pizza % n == 0) return answer = i;
        i++;
    }
    return answer;
}
```

### 35. 외계행성의 나이
```js
function solution(age) {
    var answer = '';
    const alphabet = ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j"];
    const ageArr = age.toString().split("").map(Number);
    answer += ageArr.map((age) => alphabet[age]).join("");
    return answer;
}
```

### 36. 배열 회전시키기
```js
function solution(numbers, direction) {
    var answer = [];
    if(direction == "left") {
        const leftNum = numbers.shift()
        answer.push(...numbers);
        answer.push(leftNum);
    } else {
        answer.push(numbers.pop());
        answer.push(...numbers);
    }
    return answer;
}
```

### 37. 369게임
```js
function solution(order) {
    var answer = 0;
    return order.toString().split("").filter((v) => "369".includes(v)).length;
}
```

### 38. 숫자 찾기
```js
function solution(num, k) {
    const numArr = num.toString().split("").map(Number)
    return numArr.indexOf(k) >= 0 ?  numArr.indexOf(k)+1 :  -1;
}
```
✅ String에서는 indexOf 사용 가능. int에서는 사용 불가능.


### 39. 합성수 찾기
```js
function solution(n) {
    var answer = 0;
    for(let i = 1 ; i <= n ; i++) {
        if(isChecked(i)) answer++; 
    }
    return answer;
}

function isChecked(num) {
    let cnt = 0;
    for(let i = 1 ; i <= num ; i++) {
        if(num % i == 0) cnt++;
    }
    return cnt >= 3 ? true : false;
}
```

### 40. 중복된 문자 제거
```js
function solution(my_string) {
    var answer = '';
    for(let str of my_string) {
        if(!answer.includes(str)) answer += str;
    }
    return answer;
}
```

----

## END