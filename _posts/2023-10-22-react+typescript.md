---
title: React + Typescript 프로젝트 생성하기
# author: cotes
date: 2023-10-22 11:33:00 +0800
categories: [캡스톤디자인 🎓, 개발일지]
tags: [Capston, React, Typescript]
pin: true
math: true
mermaid: true
image:
  path: /assets/img/react+typescript.jpeg
---

> react.js 와 typescript 를 활용한 프로젝트를 만들어보겠습니다.

## **1. 리액트 프로젝트 생성**
--------------------------
먼저 **`create-react-app`** 을 이용해 리액트 어플리케이션을 만들어줍니다.<br>
```terminal
npx create-react-app [프로젝트 명] --template typescript
```
**`--template typescript`** 라는 속성은 <i>**"타입스크립트 언어를 기반으로 리액트 환경을 구성할 것이다"**</i> 라는 의미입니다.

```terminal
cd [프로젝트 명]
npm start  // 또는 yarn start
```
프로젝트 폴더로 이동한 후, npm start 명령어를 통해 생성된 리액트 프로젝트를 실행시켜 정상적으로 동작하는 지 확인할 수 있다. (`localhost:3000`{: .filepath} 포트에서 확인가능)
![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/c2dcf6e7-5cde-4309-88f9-a6b02824bbea)
<i>**"Would you like to run the app on another port instead?"**</i> 질문에는 Y 를 입력해주면 된다.

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/7ce19ff6-8ca6-436e-bd22-739afff8d631)

<br>

## **2. 폴더 구조**
-------------------------
> 추후에 포스팅 예정