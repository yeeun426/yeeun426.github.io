---
title: "JS 알고리즘 입문 20문제 (100문제 완료)"
categories: [Ureca, Algorithm]
tags: [javascript, algorithm]
image:
  path: /assets/post/2025/ureca/algorithmBeginner4.png
  alt: JS
published: true
---

### 1. 외계어 사전
```js
function solution(spell, dic) {
    const spellStr = spell.sort().join("");    
    for(let str of dic) {
        if(str.split("").sort().join("").includes(spellStr)) return 1;
    }
    return 2;
}
```

### 2. 종이 자르기
```js
class Solution {
    public int solution(int M, int N) {
        return (M-1) + (N-1) * M;
    }
}
```

### 3. 직사각형 넓이 구하기
```js
function solution(dots) {
    dots.sort((a,b) => a[0] - b[0]);
    return Math.abs((dots[0][1] - dots[1][1]) * (dots[2][0] - dots[1][0]));
}
```

### 4. 로그인 성공?
```js
function solution(id_pw, db) {    
    for(let value of db) {
        if(value[0] == id_pw[0] && value[1] == id_pw[1]) {
            return "login"
        } else if (value[0] == id_pw[0] && value[1] !== id_pw[1]) {
            return "wrong pw"
        }
    }
    return "fail";
}
```

### 5. 치킨 쿠폰
```js
function solution(chicken) {
    var answer = 0
    while (chicken > 9) {
        answer += parseInt(chicken / 10)
        chicken = parseInt(chicken / 10) + chicken % 10;
    }
    return answer;
}
```

### 6. 등수 매기기
```js
function solution(score) {
    var answer = new Array(score.length).fill(0);
    const average = [];
    
    for(let idx in score) {
        average.push([Number(idx), (score[idx][0] + score[idx][1]) / 2])
    }
    average.sort((a,b) => b[1] - a[1]);
    
    let curRank = 1;
    for(let i = 0 ; i < average.length ; i++) {
        if(i > 0 && average[i][1] == average[i-1][1]) {
            answer[average[i][0]] = answer[average[i-1][0]]
        } else {
            answer[average[i][0]] = curRank;
        }
        curRank++;
    }
    return answer;
}

// 다른 사람 풀이
function solution(score) {
    let avg = score.map(v=>(v[0]+v[1])/2);
    let sorted = [...avg].sort((a,b)=>b-a);
    return avg.map(v=>sorted.indexOf(v)+1);
}
```

### 7. 저주의 숫자 3
```js
function solution(n) {
    let answer = 1;
    let count = 1;
    
    while (count < n) {
        answer++; 
        if (!answer.toString().includes("3") && answer % 3 !== 0) {
            count++;
        }
    }
    return answer;
}
```

### 8. 다음에 올 숫자
```js
function solution(common) {
    if(common[1] - common[0] == common[common.length-1] - common[common.length-2]) {
        return common[common.length-1] + (common[1] - common[0])
    } else {
        return common[common.length-1] * (common[1] / common[0])
    }
}
```

### 9. 최빈값 구하기
```js
function solution(array) {
    var answer = 0;
    const cntObj = {}
    
    for(let i = 0 ; i < array.length ; i++) {
        cntObj[array[i]] = (cntObj[array[i]] || 0) + 1;
    }
    
    const sorted = Object.entries(cntObj).sort((a, b) => b[1] - a[1]); // entries : 객체를 배열로 변환
    return (sorted.length > 1 && sorted[0][1] === sorted[1][1]) ? -1 : Number(sorted[0][0]);
}
```

### 10. 유한소수 판별하기
```js
function solution(a, b) {
    function gcd(x, y) {
        return y === 0 ? x : gcd(y, x % y);
    }
    
    let g = gcd(a, b);
    b /= g;
    
    while (b % 2 === 0) b /= 2;
    while (b % 5 === 0) b /= 5;
    
    return b === 1 ? 1 : 2;
}
```

### 11. 문자열 밀기
```js
function solution(A, B) {
    if(A == B) return 0;
    return (B + B).indexOf(A);
}
```

### 12. 특이한 정렬
```js
function solution(numlist, n) {
    const close = numlist.map(el => el - n);
    const sorted = [...close].sort((a,b) => Math.abs(a)-Math.abs(b) || b - a);
    return sorted.map((el) => numlist[close.indexOf(el)]);
}
```

### 13. 다항식 더하기
```js
function solution(polynomial) {
    var answer = ''
    const polyArr = polynomial.split(" + ");
    
    let x = 0;
    let num = 0;
    for(let p of polyArr) {
        if(p.includes("x")) {
            x += Number(p.split("x")[0]) || 1
        } else {
            num += Number(p)
        }
    }
    
    if (x > 0) answer += (x === 1 ? "x" : x + "x");
    if (num > 0) answer += (answer ? " + " : "") + num;
    
    return answer;
}
```

### 14. OX 퀴즈
```js
function solution(quiz) {
    var answer = [];
    
    for(let q of quiz) {
        const[a, op, b, eq, ans] = q.split(" ");
        if(op == "+" && Number(a) + Number(b) == Number(ans)) {
            answer.push("O");
        } else if(op == "-" && Number(a) - Number(b) == Number(ans)) {
            answer.push("O");
        } else {
            answer.push("X")
        }
    }
    return answer;
}
```

### 15. 연속된 수의 합
```js
function solution(num, total) {
    var answer = []; 
    let sum = (num * (num + 1)) / 2;
    let start = 1;

    while(sum !== total) {
        if(sum < total) {
            sum -= start++;
            sum += (start + num - 1);
        } else {
            sum -= (start + num - 1);
            sum += --start;
        }
    }      
    for (let i = 0; i < num; i++) {
        answer.push(start + i);
    }
    return answer;
}
```

### 16. 분수의 덧셈
```js
function solution(numer1, denom1, numer2, denom2) {
    var answer = [];
    function gcd(x, y) {
        return y === 0 ? x : gcd(y, x % y);
    }
    let lcm = (denom1 * denom2) / gcd(denom1, denom2);
    let numerator = numer1 * (lcm / denom1) + numer2 * (lcm / denom2);

    // 기약분수로 변환하기 위한 최대공약수 계산
    let commonGCD = gcd(numerator, lcm);
    
    // 기약분수로 나누기
    numerator /= commonGCD;
    lcm /= commonGCD;
    
    answer.push(numerator);
    answer.push(lcm); 
    
    return answer;
}
```

### 17. 안전지대
```js
function solution(board) {
    var answer = 0;
    let n = board.length;

    let dx = [0, 1, 1, 1, 0, -1, -1, -1]
    let dy = [-1, -1, 0, 1, 1, 1, 0, -1]

    for (let x = 0; x < n; x++) {
        for (let y = 0; y < n; y++) {
            if (board[x][y] === 1) {
                for (let i = 0; i < 8; i++) {
                    const newX = x + dx[i];
                    const newY = y + dy[i];

                    if (newX >= 0 && newX < n && newY >= 0 && newY < n && board[newX][newY] === 0) {
                        board[newX][newY] = 2;
                    }
                }
            }
        }
    }
    
    answer = board.map(row => row.filter(value => value === 0).length).reduce((a, c) => a + c, 0)

    return answer;
}
```

### 18. 겹치는 선분의 길이
```js
function solution(lines) {
    let arr = new Array(201).fill(0);
    
    for (let [start, end] of lines) {
        for (let i = start; i < end; i++) {
            arr[i + 100]++;
        }
    }
    return arr.filter(v => v > 1).length;
}
```

### 19. 평행
```js
function solution(dots) {
    const [[x1, y1], [x2, y2], [x3, y3], [x4, y4]] = dots;
    
    function isParallel(x1, y1, x2, y2, x3, y3, x4, y4) {
        return (y2 - y1) * (x4 - x3) === (y4 - y3) * (x2 - x1);
    }

    if (isParallel(x1, y1, x2, y2, x3, y3, x4, y4)) return 1;
    if (isParallel(x1, y1, x3, y3, x2, y2, x4, y4)) return 1;
    if (isParallel(x1, y1, x4, y4, x2, y2, x3, y3)) return 1;

    return 0;
}
```

### 20. 옹알이(1)
```js
function solution(babbling) {
    let answer = 0;
    for(let b of babbling) {
        let str = b;
        for (const i of ["aya", "ye", "woo", "ma"]){
            str = str.replaceAll(i, "1");
        }
        if (/^[1]+$/.test(str)) answer += 1; // "1"로만 이루어진 경우 카운트
    }
    return answer;
}
```

--- 

## 머쓱이 스탬프 - 입문
<img src="/assets/post/2025/ureca/algorithmBeginner4.png" alt='' width=1300px>

드디어 매일 20문제에서 벗어났다 ,, <br/>
하루에 20문제를 풀어야하니깐 마지막 쯤엔 집중력이 너무 바닥나고 문제도 어려워져서 다른 사람들 코드를 많이 참고했다.
<br/>몰랐던 문법들 정리하고 내일부턴 한문제 한문제 제대로 풀어봐야지 !

---

## END
