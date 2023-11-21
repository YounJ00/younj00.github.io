---
title: "React 프로젝트 Github Pages에 배포하기"
# author: younJ00
date: 2023-11-19 11:33:00 +0800
categories: [Git 🌱, Github Pages]
tags: [Github]
pin: true
math: true
mermaid: true
image:
  path: /assets/img/github_pages_logo.jpg
---

> React 프로젝트를 Githuh Pages에 배포하는 방법을 포스팅해 볼 것이다. 이 과정에서 생긴 오류를 해결한 방법에 대해서도 정리해보겠다.

## **1. 레포지토리에서 Pages 설정하기**

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/dff2d185-002c-4c9c-af89-7d61c56da04d)

본인의 react 프로젝트가 있는 레포지토리의 **Setting 에서 Pages**를 선택해준다.<br> 그 다음 **Source 에서 아무 branch 를 골라 Save**를 하면 Published 될 준비가 되었다는 안내와 함꼐 **URL**이 나온다. 이 URL를 복사해두자.

## **2. React 프로젝트에 gh-pages 설치하기**

React 프로젝트에 아래 명령어를 사용하여 gh-pages 라이브러리를 설치해준다.

``` terminal
npm install gh-pages --save-dev
```
## **3. package.json 파일 수정하기**

📁 **파일 위치** : **`react 프로젝트 폴더/package.json`**

스크립트에 deploy를 추가해준다. 
``` json
   "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "storybook": "storybook dev -p 6006",
    "build-storybook": "storybook build",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"   // 이 부분 추가!!
  },
```
![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/92b1b279-e4f5-46dc-847d-5698ce11b98c)


homepage를 추가해주고, 주소는 앞에서 복사한 URL 주소를 넣어준다.
``` json
 "homepage": "https://capstone-cogrow.github.io/cogrow/"
```
![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/d8da2ca9-8273-47cc-8d3c-47ef7a392941)


## **4. gh-pages 배포하기**

터미널에서 아래 명령어을 실행시켜 배포를 해준다.

``` terminal
npm run deploy
```

그러면 자동으로 빌드를 해주며, github 원격 저장소에 배포에 필요한 파일을 업로드해준다.

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/3cb1825f-255d-41f9-8f3d-b0b2db946738)

다시 레포지토리에 들어가보면 gh-pages 라는 브랜치가 새롭게 만들어진 것을 확인할 수 있고, 빌드에 필요한 파일들이 업로드 되어있다.


## **5. 깃 레포지토리 다시 설정하기**

마지막으로 다시 레포지토리의 **Setting 에서 Pages**에 들어가서 브랜치를 gh-pages로 설정하고 저장해준다.

![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/c075bffb-54bd-4ca9-8bbd-dc7312e1f282)

그리고 **"Visit site"** 를 클릭해 배포된 사이트에 접속해준다.
![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/b870b920-e0e8-4023-a59e-509651b29f3a)

하지만 404오류가 떴다,, 호스팅 되는 데 5~10분 정도 소요된다고해서 기다렸는데도 오류는 해결되지 않았다.
![image](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/bccaa5ca-18ce-4c94-8d32-2043dbd8262e)


> 오류 해결 과정은 다음 포스팅에서...