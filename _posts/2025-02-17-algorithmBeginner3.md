---
title: "JS 알고리즘 입문 20문제"
categories: [Ureca, Algorithm]
tags: [javascript, algorithm]
image:
  path: /assets/post/2025/ureca/algorithmJS.jpeg
  alt: JS
published: true
---

### 1. 모스부호 (1)
```js
function solution(letter) {
    var answer = '';
    const morse = { 
    '.-':'a','-...':'b','-.-.':'c','-..':'d','.':'e','..-.':'f',
    '--.':'g','....':'h','..':'i','.---':'j','-.-':'k','.-..':'l',
    '--':'m','-.':'n','---':'o','.--.':'p','--.-':'q','.-.':'r',
    '...':'s','-':'t','..-':'u','...-':'v','.--':'w','-..-':'x',
    '-.--':'y','--..':'z'
    }    
    return letter.split(" ").map((v) => morse[v]).join("");
}
```

### 2. 2차원으로 만들기
```js
function solution(num_list, n) {
    var answer = Array.from({ length: num_list.length / n }, () => []);
    
    for (let i = 0; i < num_list.length; i++) {
        answer[Math.floor(i / n)].push(num_list[i]);
    }
    return answer;
}
```

### 3. k의 개수
```js
function solution(i, j, k) {
    var answer = 0;
    for(let num = i ; num <= j ; num++) {
        const arr = num.toString().split("");
        answer += arr.filter(ele => k.toString() === ele).length;
    }
    return answer;
}

// 다른 사람 풀이 (어떤 원리인지는 잘 모르겠다,,)
function solution(i, j, k) {
    let a ='';
    for(i;i<=j;i++){
        a += i;
    }
    return a.split(k).length-1;
}
```

### 4. A로 B만들기
```js
function solution(before, after) {
    return before.split("").sort().join("") == after.split("").sort().join("") ? 1 : 0;
}
```

### 5. 진료 순서 정하기
```js
function solution(emergency) {
    var answer = [];
    const sortEmergency = [...emergency].sort((a,b) => b-a);
    return emergency.map((value) => sortEmergency.indexOf(value)+1);
}
```

### 6. 숨어있는 숫자의 덧셈 (2)
```js
function solution(my_string) {
    const regex = /\d+/g;
    const matches = my_string.match(regex);

    if (!matches) return 0;
    return matches.reduce((acc, curr) => acc + parseInt(curr), 0);
}

// 다른 사람 풀이
function solution(my_string) {
  return my_string.split(/\D+/).reduce((acc, cur) => acc + Number(cur), 0);
}
```

### 7. 가까운 수
```js
function solution(array, n) {
    var answer = 0;
    let min = 100;
    for(let num of array.sort((a,b) => a-b)) {
        if(Math.abs(num - n) < min) {
            min = Math.abs(num - n);
            answer = num;
        }
    }
    return answer;
}
```

### 8. 팩토리얼
```js
function solution(n) {
    let answer = 0;
    let factorial = 1;
    let i = 1;
    
    while(n < factorial) {
        factorial *= i++;
        if(n < factorial) return answer
        answer++;
    }
    return answer;
}
```

### 9. 한 번만 등장한 문자
```js
function solution(s) {
    const answer = [];
    const obj = {};
    
    for(let str of s) {
        if(obj[str]) obj[str]++;
        else obj[str] = 1;
    }
    
    for(let key in obj) {
        if(obj[key] == 1) answer.push(key);
    }
    return answer.sort().join("");
}

// 다른 사람 풀이
function solution(s) {
    let res = [];
    for (let c of s) {
        if (s.indexOf(c) === s.lastIndexOf(c)) res.push(c);
    }
    return res.sort().join('');

}
```

### 10. 7의 개수
```js
function solution(array) {
    return array.join("").split("7").length - 1;
}
```

### 11. 컨트롤 제트
```js
function solution(s) {
    var answer = 0;
    const arr = s.split(" ");
    
    for(let i = 0 ; i < arr.length ; i++) {
        if(arr[i] == "Z") {
            answer -= Number(arr[i-1]);
        } else {
            answer += Number(arr[i]);
        }
    } 
    return answer;
}
```

### 12. 소인수 분해
```js

```

### 13. 이진수 더하기
```js

```

### 14. 잘라서 배열로 저장하기
```js
function solution(my_str, n) {
    const regex = new RegExp(`.{1,${n}}`, 'g');
    return my_str.match(regex);
}
```

### 15. 공 던지기
```js
function solution(numbers, k) {
    var answer = 0;
    let cnt = 0;
    let i = 0;
    while (cnt != k) {
        cnt++;
        answer = numbers[i];
        i = (i+2) % numbers.length;
    }
    return answer;
}

// 다른 사람 풀이
function solution(numbers, k) {
    return numbers[((2 * (k -1))) % numbers.length];
}
```

### 16. 문자열 계산하기
```js

```

### 17. 삼각형의 완성조건(2)
```js

```

### 18. 영어가 싫어요
```js

```

### 19. 구슬을 나누는 경우의 수
```js

```

### 20. 캐릭터의 좌표
```js

```

---

## END