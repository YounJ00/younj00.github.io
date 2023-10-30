---
title: React 에서 Node.js 서버에 데이터 요청하기 (2)
# author: cotes
date: 2023-10-29 00:00:00 +0800
categories: [캡스톤디자인 🎓, 개발일지]
tags: [Capston, React, Typescript]
pin: true
math: true
mermaid: true
image:
  path: /assets/img/react-nodejs.png
---

> [React 에서 Node.js 서버에 데이터 요청하기 (1)](https://younj00.github.io/posts/react%EC%97%90%EC%84%9C-nodeJS%EC%97%90-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%9A%94%EC%B2%AD-(1)/) <br>
이전 포스팅에서 서버 코드를 작성해보고, 테스트해봤다. <br>
이번 포스팅에서는 프론트 부분을 완성하여 프론트에서 서버로 데이터 요청을 해볼 것이다.


## **1. 리액트 프로젝트 생성**
------------------------------

먼저 아래 명령을 통해 client 폴더에 **리액트 프로젝트**를 생성해줍니다.

```terminal
cd client
npx create-react-app .
```

처음에 **create-react-app** 을 하고나면 여러가지 많은 파일들이 생성되는데, 이 중에서 내가 사용하지 않을 불필요한 파일들을 삭제해줍니다.

- **`App.css`**
- **`App.test.js`**
- **`index.css`**
- **`logo.svg`**

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/eebc1093-01fe-4883-82a0-f7390860c752)

그 다음 **App.js** 코드를 아래와 같이 수정해줍니다.<br>
간단하게 테스트해보기 위해 **TODOLIST 텍스트**를 띄워주겠습니다.

📁 **파일 경로** : **`request_Test/client/src/App.js`{: .filepath}**

```javascript
function App() {
  return (
    <div className="App">
      <h1>TODOLIST</h1>
    </div>
  );
}

export default App;
```

코드 입력 후, 아래 명령으로 리액트 프로젝트 서버를 실행시켜 줍니다.

```terminal
npm start
```
![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/80f0cdbd-758d-4e7d-8da2-e5438c32a1dd)

자동으로 포트 3001을 지정해주어 <i>**localhost:3001**</i> 에서 확인이 가능하다.

<br>

## **2. nodejs 서버에 데이터 요청**
------------------------------

### **◾ fetch 사용**

```javascript
function App() {
  fetch('http://localhost:3000/api/todo')
    .then((response) => response.json())
    .then((data) => console.log(data));
    
  return (
    <div className="App">
      <h1>TODOLIST</h1>
    </div>
  );
}

export default App;
```

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/07af2903-681c-44e5-a915-88c145ae9990)

> **`"CORS"`** 오류 발생함,,
{: .prompt-danger }
> **CORS** 오류 발생 이유는 현재 서버주소를 보면<br>
**`server: localhost:3000`** <br>
**`client: localhost:3001`** <br>
이기 때문에 두 서버는 서로 **host와 port를 포함한 데이터의 출처인 Origin이 다르기 때문**에 데이터 이동에 제한이 생긴다.
{: .prompt-info }
> 나는 아래 **`"npm build"`**를 통해 오류를 해결했다.
{: .prompt-tip }


```terminal

```


### **◾ axios 사용**