---
title: Styled Components 사용하여 컴포넌트 디자인하기
# author: cotes
date: 2023-10-22 11:35:00 +0800
categories: [프로젝트 🎓, 캡스톤디자인]
tags: [Capston, React, Typescript]
pin: true
math: true
mermaid: true
image:
  path: /assets/img/styled-components.png
---

## **styled-components 란?**
------------------------------

> 기존 돔을 만드는 방식인 css, scss 파일을 밖에 두고, 태그나 id, class이름으로 가져와 쓰지 않고, **동일한 컴포넌트에서 컴포넌트 이름을 쓰듯 스타일을 지정하는 것을 "styled-components"** 라고 부릅니다.<br>
css 파일을 밖에 두지 않고, 컴포넌트 내부에 넣기 때문에, css가 전역으로 중첩되지 않도록 만들어주는 장점이 있습니다

<br>

## **패키지 설치**
------------------------------
**styled-components** 라는 **NPM 패키지명**을 가지고 있어서, React 프로젝트에 아래와 같이 **npm 커맨드**로 간단히 설치할 수 있습니다.

```terminal
npm i styled-components
```
![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/bf190e87-e1b7-40d9-8d60-6cbf51a7222f)

설치 후에 **/package.json** 에 **styled-components** 가 추가된 것을 확인할 수 있습니다.
```json
"dependencies": {
    "@testing-library/jest-dom": "^5.17.0",
    "@testing-library/react": "^13.4.0",
    "@testing-library/user-event": "^13.5.0",
    "@types/jest": "^27.5.2",
    "@types/node": "^16.18.59",
    "@types/react": "^18.2.31",
    "@types/react-dom": "^18.2.14",
    "react": "^18.2.0",
    "react-docgen-typescript-loader": "^3.7.2",
    "react-dom": "^18.2.0",
    "react-scripts": "5.0.1",
    "styled-components": "^6.1.0", // 추가됨!
    "typescript": "^4.9.5",
    "web-vitals": "^2.1.4"
  }
```
{: file='package.json'}

<br>

## **기본 문법**
------------------------------
> 추후에 포스팅 예정