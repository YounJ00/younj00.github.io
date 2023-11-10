---
title: React 에서 Node.js 서버에 데이터 요청하기 (2)
# author: cotes
date: 2023-10-29 00:00:00 +0800
categories: [프로젝트 🎓, 캡스톤디자인]
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

## **2. nodejs 서버에 데이터 요청 (fetch)**
------------------------------

이제 리액트에서 서버로 데이터 요청을 해보자.<br>
방법은 **fetch** 와, **axios** 가 있는데 두 가지 방법 모두 해보겠다.

### **◾ 데이터 요청**

fetch 를 사용하면 별도로 설치할 필요 없이 간편하게 이용할 수 있다.

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

코드 작성 후 **npm start** 로 실행시켜준다.

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/07af2903-681c-44e5-a915-88c145ae9990)

> 하지만 **`"CORS"`** 오류 발생함,,
{: .prompt-danger }
> **CORS** 오류 발생 이유는 현재 서버주소를 보면<br>
**`server: localhost:3000`** <br>
**`client: localhost:3001`** <br>
위 처럼 두 서버는 서로 **host와 port를 포함한 데이터의 출처인 Origin이 다르기 때문**에 데이터 이동에 제한이 생긴다.
{: .prompt-info }
> 오류를 해결하기 위해서는 **서버에 CORS 정책을 허용**해주어야 합니다.
{: .prompt-tip }


```terminal
npm install cors
```
위 명령을 통해 cors 를 설치하고 server.js 를 수정해준다.

```javascript
const express = require('express');
const app = express();

/** 이 부분 추가됨!! **/
const cors = require('cors');
app.use(cors());
/** 이 부분 추가됨!! **/

app.use(express.json());
app.use(express.urlencoded({ extended: true }));

let id = 2;
const todoList = [{
    id: 1,
    text: '할일 1',
    done: false,
    },
];

app.get('/api/todo', (req, res) => {
    res.json(todoList);
});

app.post('/api/todo', (req, res) => {
    const { text, done } = req.body;
    todoList.push({
        id: id++,
        text,  
        done,
    });
    return res.send('success');
});

app.listen(3000, () => {
    console.log('server start!!');
});
```

서버를 다시 실행시키고 확인해보자!!

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/0cc2ac71-9be9-43d4-be63-fc166106b24b)

서버에서 리액트로 데이터를 잘 가져오는 것을 확인할 수 있다.

### **◾ 데이터 렌더링**

```javascript
import { useEffect, useState } from "react";

function App() {
  const [todoList, setTodoList] = useState(null);

  useEffect(() => {
     fetch('http://localhost:3000/api/todo')
      .then((response) => response.json())
      .then((data) => setTodoList(data));
  }, []);
 
  return (
    <div className="App">
      <h1>TODOLIST</h1>
      {todoList && todoList.map((todo) => (
        <div key={todo.id}>
          <div>{todo.id}</div>
          <div>{todo.text}</div>
          <div>{todo.done ? 'Y' : 'N'}</div>
        </div>
      ))}
    </div>
  );
}

export default App;
```

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/4e48c423-0d79-4fc2-b351-b897cfd70270)


### **◾ 데이터 POST**

```javascript
import { useEffect, useState } from "react";

function App() {
  const [todoList, setTodoList] = useState(null);

  const fetchData = () => {
    fetch('http://localhost:3000/api/todo')
      .then((response) => response.json())
      .then((data) => setTodoList(data));
  };

  useEffect(() => {fetchData()}, []);

  const onSubmitHandler = (e) => {
    e.preventDefault();
    const text = e.target.text.value;
    const done = e.target.done.checked;

    fetch('http://localhost:3000/api/todo', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        text,
        done,
      }),
    }).then(() => fetchData());
  };
 
  return (
    <div className="App">
      <h1>TODOLIST</h1>
      <form onSubmit={onSubmitHandler}>
        <input name="text"/>
        <input name="done" type='checkbox'/>
        <input type="submit" value="추가" />
      </form>
      {todoList?.map((todo) => (
        <div key={todo.id} style={{display: 'flex'}}>
          <div>{todo.id}</div>
          <div>{todo.text}</div>
          <div>{todo.done ? 'Y' : 'N'}</div>
        </div>
      ))}
    </div>
  );
}

export default App;
```

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/b93c5cc0-4f73-45c3-9e23-00f929d9286a)

<br>

## **3. nodejs 서버에 데이터 요청 (axios)**
------------------------------

먼저 아래 명령어를 통해 client 프로젝트에 axios 라이브러리를 설치해줍니다.

```terminal
npm install axios
```

axios 라이브러리를 사용하면 코드를 좀 더 직관적으로 짤 수 있다.

```javascript
import { useEffect, useState } from "react";
import axios from 'axios';

const SERVER_URL = 'http://localhost:3000/api/todo';

function App() {
  const [todoList, setTodoList] = useState(null);

  const fetchData = async () => {
    const response = await axios.get(SERVER_URL);
    setTodoList(response.data);

    //fetch('http://localhost:3000/api/todo')
    //  .then((response) => response.json())
    //  .then((data) => setTodoList(data));
  };

  useEffect(() => {fetchData()}, []);

  const onSubmitHandler = async (e) => {
    e.preventDefault();
    const text = e.target.text.value;
    const done = e.target.done.checked;
    axios.post(SERVER_URL, {text, done});
    fetchData();

    // fetch('http://localhost:3000/api/todo', {
    //  method: 'POST',
    //  headers: {
    //    'Content-Type': 'application/json'
    //  },
    //  body: JSON.stringify({
    //    text,
    //    done,
    //  }),
    // }).then(() => fetchData());
  };
 
  return (
    <div className="App">
      <h1>TODOLIST</h1>
      <form onSubmit={onSubmitHandler}>
        <input name="text"/>
        <input name="done" type='checkbox'/>
        <input type="submit" value="추가" />
      </form>
      {todoList?.map((todo) => (
        <div key={todo.id} style={{display: 'flex'}}>
          <div>{todo.id}</div>
          <div>{todo.text}</div>
          <div>{todo.done ? 'Y' : 'N'}</div>
        </div>
      ))}
    </div>
  );
}

export default App;
```

axios 를 사용한 코드도 잘 작동되는 것을 확인할 수 있다.

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/9429b14d-b01c-4c68-bec5-33064aed606f)