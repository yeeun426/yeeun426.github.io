---
title: "[Tech] Web Storage 그리고 cookie" 
categories: [Web, CS]
tags: [cookie, session storage, local storage]
image:
  path: /assets/post/2025/web/webstorage.png
  alt: sql
published: true
---

## Cookie
Cookie는 서버와 클라이언트가 지속적으로 데이터를 교환할 수 있도록 만들어진 작은 데이터 조각이다.      
서버가 사용자의 웹 브라우저에 Cookie를 전송하면 브라우저는 이를 저장하고, 이후 Backend API 요청 시 자동으로 쿠키 데이터를 함께 전송한다.

### Cookie의 문제점
1. 트래픽 증가: HTTP Header의 Set-Cookie를 통해 매 요청마다 데이터가 전송되어 트래픽이 증가하고 성능이 저하될 수 있음.
2. 보안 취약점: XSS(스크립트를 통한 해킹) 공격 등에 의해 쿠키가 유출될 위험이 있음.
3. 제한된 저장 공간: 쿠키는 약 4KB까지만 저장 가능함.

# 웹 스토리지 (Web Storage)
보통 정보 저장은 서버에서 Database에 저장하지만, 클라이언트에 데이터를 저장할 수 있도록 지원하는 기능이다. 

## 1. Local Storage
- 브라우저에 반영구적으로 데이터를 저장
- localStorage는 시간제한이 없고 브라우저가 꺼져도 죽지 않는다
  + JavaScript 코드나 브라우저 캐시 또는 로컬 저장 데이터를 지워야만 사라진다.
- 도메인 (domain)이 다르면 접근 불가
  - 예) www.google.com에서 로컬 스토리지에 저장한 데이터를 www.example.com에서 접근할 수 없음 
<img src="/assets/post/2025/web/webStorage2.png" alt='https://developer.chrome.com/docs/devtools/storage/localstorage/?utm_source=devtools' width=1200px>

```js
localStorage.setItem('name', 'suzy'); // key와 value 형태로 저장
localStorage.getItem('name'); // 데이터 불러오기
localStorage.removeItem('name'); // 키(key)에 해당하는 값을 삭제
localStorage.clear(); // 다 삭제
```

✅ 그래서 언제 쓰일 수 있나 ? ㅈ다크모드를 설정 후, 재방문 시 이전 모드가 자동으로 설정되도록 localStorage에 저장!

출처: https://bo5mi.tistory.com/213 [대범하게:티스토리]
### 2. Session Storage
- 각각의 세션(브라우저 탭을 새로 열면 새로운 세션)마다 개별적으로 데이터가 저장됨
  - 예) 브라우저에서 여러개의 탭을 실행하면 탭마다 새로운 세션
- 브라우저나 탭이 종료될 때 데이터가 자동으로 삭제됨.
- 같은 도메인이라도 세션이 다르면 데이터 접근 불가

<img src="/assets/post/2025/web/webStorage3.png" alt='https://developer.chrome.com/docs/devtools/storage/sessionstorage/' width=1200px>

```js
sessionStorage.setItem("email", email); // 데이터 저장
const email = sessionStorage.getItem("email"); // 데이터 불러오기
```

## Cookie vs Web Storage

| 항목 | Cookie | Web Storage (Local & Session) |
|------|--------|---------------------------|
| 저장 방식 | 문자열(String) | key-value 방식 |
| 저장 공간 | 4KB | 약 5MB |
| 데이터 유지 | 설정된 만료 시간까지 | Local: 영구적, Session: 브라우저 종료 시 삭제 |
| 서버 전송 여부 | 모든 HTTP 요청에 포함됨 | 서버와 전혀 통신하지 않음 |

<img src="/assets/post/2025/web/webstorage1.png" alt='https://www.loginradius.com/blog/engineering/guest-post/local-storage-vs-session-storage-vs-cookies/' width=1300px>


---

## Reference
이 포스트는 아래 게시글의 정보 및 이미지가 사용되었습니다.
1. [mdn Web Storage API](https://developer.mozilla.org/ko/docs/Web/API/Web_Storage_API)
2. [local storage vs session storage vs cookies](https://www.loginradius.com/blog/engineering/guest-post/local-storage-vs-session-storage-vs-cookies/)

---

## END