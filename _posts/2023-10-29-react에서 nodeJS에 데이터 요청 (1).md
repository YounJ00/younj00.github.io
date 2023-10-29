---
title: React 에서 Node.js 서버에 데이터 요청하기 (1)
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

> 프론트에서 서버에 데이터 요청하는 방법에 대해 공부한 것 정리.<br>
프론트는 **React** 를 사용했고, 서버는 **Node.js** 를 사용했다.

## **1. 프로젝트 생성**
------------------------------

먼저 프로젝트를 생성할 폴더를 만들고, 그 안에 **프론트** 폴더와 **서버** 폴더를 추가로 만들어준다.<br>
나는 **request_Test** 폴더를 만들어 그 안에 **client, server** 폴더를 만들어주었다.

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/ecfbc19c-41b8-4fb7-af8b-30a5011486d4)

<br>

## **2. Server 구축**
------------------------------

### **◾ npm init**

먼저 위에서 만들었던 **server** 폴더로 이동해서 **nodejs 프로젝트**를 만들어준다.

```terminal
cd request_Test/server
npm init
```

그러면 server 폴더에 **package.json** 파일이 생성된 것을 확인할 수 있다.

그 다음 **express**를 사용하기 위해 아래 명령어로 **express**를 설치해줍니다.

```terminal
npm install express
```

### **◾ server.js 파일 생성**

server 폴더에 server.js 파일을 만들어서 서버 코드를 짜줍니다.<br>
📁 **파일 경로** : **`request_Test/server/server.js`{: .filepath}**

```javascript
const express = require('express');
const app = express();

app.get('/', function (req, res) {
    res.send('Hello World');
});

app.listen(3000, () => {
    console.log('server start!!');
});
```
위 express 샘플 코드를 작성하여 서버가 잘 작동하는 지 확인해볼 수 있다. <br>
아래 명령을 실행하면 콘솔에는 'server start!!' 메시지가 출력되고, 3000번 포트에서는 'Hello World' 출력으로 서버가 잘 작동하는 지 확인할 수 있다.

```terminal
node server.js
```
![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/8a134a15-8cc8-4e8b-9946-33702a51d372)




