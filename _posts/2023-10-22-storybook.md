---
title: react 개발을 위한 Storybook 활용하기
# author: cotes
date: 2023-10-22 11:34:00 +0800
categories: [캡스톤디자인 🎓, 개발일지]
tags: [Capston, React]
pin: true
math: true
mermaid: true
image:
  path: /assets/img/storybook.png
---

> <i>**Storybook**</i> 은 독립적인 컴포넌트를 개발할 수 있으며, 컨포넌트를 조합해 Story 에서 테스트해볼 수 있다.<br> 
React 개발에 유용하게 쓰이고 있기 떄문에 사용하게 되었다.

## **1. 스토리북 설치**
-------------------------
먼저 Storybook 사용하기 위한 초기세팅을 해줍니다.

```terminal
npx sb init  // 초기세팅
npm add --dev react-docgen-typescript-loader  // 컴포넌트 테이블을 만들기 위해 설치함
```
![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/faf58e7b-470c-4b39-a514-b5c8cc082c56)

1~2분 정도 걸려 위 같이 출력되었다면 설치 끝!!<br>
설치가 완료되었다면 아래 명령어를 통해 실행해보겠습니다. (`localhost:6006`{: .filepath} 포트에서 확인가능)
```terminal
npm run storybook  // or yarn storybook
```
![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/cf1feeec-b052-48ff-b062-f7a94d445b3b)

<br>

## **2. 폴더 구조**
-------------------------
> 추후에 포스팅 예정

<br>

## **3. 스토리 만들기**
-------------------------
> 추후에 포스팅 예정