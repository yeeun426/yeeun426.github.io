---
title: React Bootstrap 사용 후, &#35;Tab &#35;onSelect
categories: [Frontend, CSS]
tags: [bootstrap, tab, onSelect]
image:
  path: /assets/post/2025/css/ReactBootstrap.jpg
  alt: ReactBootstrap
published: true
---

LG 유플러스 유레카 교육과정을 들으며, 설 연휴 기간동안 자기소개 웹 페이지 제작을 과제로 받았다.<br/>
기존의 포트폴리오에서 디자인을 따와서 수업 중에 배운 bootstrap을 적용해 수정했다.
그렇게 bootstrap과 js를 함께 사용하다보니 부트스트랩의 원리를 알아야 수정할 수 있는 난관에 부딪혔다.
이 내용에 대해 정리해보려고 한다.

---

``` js
export default function Popup() {
  return (
    <div className='mainIntro-wrapper'>
      <PopupStyled>
        <Container>
          <Tab.Container id='left-tabs-example' defaultActiveKey='1'>
            <div className='popup-left'>
              <Row>
                <Col>
                  <Nav variant='pills' className='flex-column'>
                    <Nav.Item>
                      <Nav.Link eventKey='1'>🏠 home</Nav.Link>
                    </Nav.Item>
                    <Nav.Item>
                      <Nav.Link eventKey='2'>🙋🏼‍♀️ about me</Nav.Link>
                    </Nav.Item>
                    <Nav.Item>
                      <Nav.Link eventKey='3'>🖥️ share</Nav.Link>
                    </Nav.Item>
                  </Nav>
                </Col>
              </Row>
            </div>
            <div className='popup-right'>
              <Col>
                <Tab.Content>
                  <Tab.Pane eventKey='1'>
                    <Hello />
                  </Tab.Pane>
                  <Tab.Pane eventKey='2'>
                    <AboutMe />
                  </Tab.Pane>
                  <Tab.Pane eventKey='3'>
                    <Share />
                  </Tab.Pane>
                </Tab.Content>
              </Col>
            </div>
          </Tab.Container>
        </Container>
      </PopupStyled>
    </div>
  );
}

function Hello() {
  return (
    <div className='popup-content'>
      <div className='pc-left'>
        <div className='pcl-title'>
          <div>안녕하세요,</div>
          <strong>이예은</strong>입니다 !
        </div>
        <div className='pcl-btns'>
          <button className='pcl-btn'>
            About Me 〉
          </button>
          <button className='pcl-btn'>
            Share 〉
          </button>
        </div>
      </div>
      <div className='pc-right'>
        <Image src='images/myimg1.png' alt='yeeun' fluid />
      </div>
    </div>
  );
}
```

내가 처음 짠 코드는 대충 이러했다. (간결한 코드를 포스팅에 삽입하고자 포스팅에 불필요한 부분은 지운 상태의 코드이다.)<br/>
내가 짜고 싶었던 코드는  <Hello /> 컴포넌트에서 .pcl-btn을 클릭했을 경우, 각각 <aboutMe>으로, <Share>로 이동하고자 했다.

<img src="/assets/post/2025/css/bootstrapEx1.png" alt='' width=1300px>

이미지에서 직접 살펴보자면 아래 버튼을 클릭했을 때 왼쪽 사이드바 해당 탭에 active가 되고 active된 탭의 내용이 떠야했다.<br/>
하지만 나는 bootstrap으로 tab을 구현했을 때문에 <Nav.Link>를 눌렀을 때 <Tab.Pane>의 컨텐츠가 뜨는 그 원리를 알아야했다.

---

### Tab의 동작 원리

탭을 누르면 내용이 바뀌는 원리는 React Bootstrap의 Tab.Container와 eventKey 속성을 활용한 상태 관리 때문이다.

1. <Tab.Container> 안에서 defaultActiveKey="1"을 설정해 초기 선택된 탭을 1번으로 지정했다.
2. <Nav.Link>에 eventKey 속성을 부여해서, 특정 탭을 클릭하면 해당 eventKey가 활성화된다.
3. <Tab.Content> 안의 <Tab.Pane>들이 각각 eventKey를 가지고 있어서, 현재 선택된 탭에 맞는 내용만 보여준다.

---

### 버튼을 눌러 탭을 변경하기 

버튼 클릭으로 탭을 바꾸려면, 현재 활성화된 탭의 상태를 변경하는 함수를 만들면 된다.

``` js
export default function Popup() {
  const [activeTab, setActiveTab] = useState("1"); // 현재 선택된 탭 상태

  return (
    <Container>
      <Tab.Container activeKey={activeTab} onSelect={(k) => setActiveTab(k)}>
        <Nav variant="pills">
          <Nav.Item>
            <Nav.Link eventKey="1">🏠 home</Nav.Link>
          </Nav.Item>
          <Nav.Item>
            <Nav.Link eventKey="2">🙋🏼‍♀️ about me</Nav.Link>
          </Nav.Item>
        </Nav>

        <Tab.Content>
          <Tab.Pane eventKey="1">
            <p>Home Content</p>
          </Tab.Pane>
          <Tab.Pane eventKey="2">
            <p>About Me Content</p>
          </Tab.Pane>
        </Tab.Content>

        <Button onClick={() => setActiveTab("1")}>Go to Home</Button>
        <Button onClick={() => setActiveTab("2")}>Go to About Me</Button>
      </Tab.Container>
    </Container>
  );
}
```

1. useState("1")을 사용해서 현재 선택된 탭을 관리한다.
2. <Tab.Container>에 activeKey={activeTab}를 주면, 상태에 따라 탭이 바뀌게 된다.
3. <Nav.Link>를 클릭하면 onSelect={(k) => setActiveTab(k)}가 실행되면서 eventKey 값을 activeTab에 반영한다.
4. 버튼을 클릭하면 setActiveTab("2") 같은 식으로 직접 탭을 바꿀 수 있게 된다.


내가 작성한 코드에서 변경하려면 이렇게 수정하면 된다.
1. Popup에서 setActiveTab을 <Hello> 컴포넌트에 props로 전달.
2. <Hello> 에서 버튼 클릭 시 setActiveTab("2"), setActiveTab("3")을 호출하면 탭이 변경됨.
3. 기존의 Tab.Container 상태(activeTab)는 그대로 유지되면서, 다른 컴포넌트에서도 탭을 컨트롤할 수 있게 된다.

---

## 두번째 의문 : <Nav.Link>를 클릭하면 onSelect가 호출되도록 bootstrap 메커니즘이 짜여져 있는건가?

결론적으로 정답은 yes 이다. <br>
React-Bootstrap의 Tab.Container 내부적으로 onSelect를 호출하도록 설계되어 있다.

### Nav.Link가 Tab.Container와 자동으로 연결되는 내부 로직

1️⃣ Nav.Link 내부 동작 원리
React-Bootstrap에서 Nav.Link는 내부적으로 NavContext(컨텍스트 API)를 사용해 Tab.Container와 통신한다.
즉, Nav.Link는 직접 onClick을 가지고 있지 않아도, eventKey를 Tab.Container에서 자동으로 감지해서 처리할 수 있다.

```jsx
<Nav.Link eventKey='1'>🏠 home</Nav.Link>
```
1. Nav.Link가 클릭됨
2. 내부적으로 NavContext를 통해 eventKey='1'을 Tab.Container에 전달
3. Tab.Container는 onSelect를 호출하면서 eventKey 값을 넘겨줌

2️⃣ NavContext가 onSelect를 실행하는 구조
React-Bootstrap의 Nav 및 Tab.Container는 NavContext라는 컨텍스트를 사용해서 연결되어 있다.

📌 즉, Nav.Link는 NavContext를 통해 Tab.Container와 소통하는 구조임.

```tsx
// React-Bootstrap 내부 코드 구조 예시 (생략된 부분 있음)
const NavContext = React.createContext(null);

function NavLink({ eventKey, onClick, ...props }) {
  const context = useContext(NavContext);

  return (
    <a
      {...props}
      onClick={(e) => {
        if (onClick) onClick(e);  // 사용자 지정 onClick 실행
        if (context && eventKey !== undefined) {
          context.onSelect(eventKey, e);  // eventKey를 onSelect로 전달
        }
      }}
    />
  );
}
```
✅ Nav.Link를 클릭하면 내부적으로 context.onSelect(eventKey)를 호출해서 Tab.Container에 eventKey를 전달함.<br>
✅ context.onSelect는 Tab.Container에서 제공하는 onSelect={(k) => setActiveTab(k)}와 연결되어 있음.<br/>
✅ 따라서, Nav.Link가 클릭되면 eventKey가 onSelect로 전달되고, activeTab 상태가 변경됨!<br/>


3️⃣ Tab.Container가 onSelect를 처리하는 구조

{% raw %}
```tsx
function TabContainer({ activeKey, onSelect, children }) {
  return (
    <NavContext.Provider value={{ activeKey, onSelect }}>
      {children}
    </NavContext.Provider>
  );
}
```
{% endraw %}

✅ Tab.Container는 NavContext.Provider를 통해 onSelect 함수를 Nav.Link에 전달함.<br/>
✅ Nav.Link를 클릭하면 onSelect(eventKey)가 실행됨.<br/>
✅ 결국 setActiveTab(eventKey)가 실행되면서 UI가 변경됨.

4️⃣ 결론: onClick 없이 onSelect가 실행되는 이유<br/>
✅ Nav.Link는 내부적으로 NavContext를 사용해 eventKey를 Tab.Container로 전달함.<br/>
✅ NavContext 안에는 onSelect 함수가 포함되어 있어서, Nav.Link 클릭 시 자동 실행됨.<br/>
✅ 따라서, Nav.Link를 클릭하면 직접 onClick을 설정하지 않아도 onSelect가 실행된다.

---

## onSelect

React-Bootstrap에서 제공하는 선택(selection) 이벤트 핸들러
기본적으로 Tab, Dropdown, Accordion, Nav 같은 선택 가능한 UI 요소에서 사용된다.

*** onSelect는 브라우저의 기본 이벤트(onSelect → 텍스트 선택 이벤트)와는 다르고, React-Bootstrap이 자체적으로 만든 핸들러임. ***


### onSelect는 언제 실행될까?
React-Bootstrap의 Nav나 Tab.Container 같은 컴포넌트에서, <Nav.Link>를 클릭하면 내부적으로 onSelect가 실행돼.

🚀 정리
- onSelect는 React-Bootstrap에서 클릭하면 선택이 변경되는 컴포넌트에서 사용
- 선택된 값을 바꿔주는 함수(setState)를 실행한다.
- eventKey를 기반으로 특정 동작을 수행할 수 있음.

->  즉, "선택(selection)"이 중요한 UI 요소에는 onSelect가 있다! 🎯

---

### Reference
이 포스트는 아래 게시글의 정보 및 이미지가 사용되었습니다.
1. [React Bootstrap tabs](https://react-bootstrap.github.io/docs/components/tabs)

---

<h2 style="text-align: center;" data-ke-size="size26"><b>END</b></h2>