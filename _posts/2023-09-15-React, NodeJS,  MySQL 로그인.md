---
title: React, NodeJS 와 MySQL 을 이용한 로그인/회원가입
author: cotes
date: 2023-09-15 11:33:00 +0800
categories: [Capston Design 👩‍🎓, 개발일지]
tags: [Capston]
pin: true
math: true
mermaid: true
image:
  path: /assets/img/back.jpg
---

<br>
express를 비롯한 Node.js의 모듈들과, React로 구현한 로그인, 회원가입 예제를 따라해볼 거다.<br>
앞 포스팅에서 설치한 MySQL을 데이터베이스로 사용한다. (<b>[MySQL 설치 및 접속](https://younj00.github.io/study/study1/)</b>)

## 1. MySQL Setting

### ✔ mysql 접속

```
mysql> mysql -u root -p
```
MySQL Server 의 bin폴더로 이동하여 mysql에 접속해준다.<br>
📁 폴더 경로 : <b>C:\Program Files\MySQL\MySQL Server 8.0\bin</b>


### ✔ 사용자 및 데이터베이스 생성

```
mysql> CREATE USER 사용자ID;   // 사용자 추가
mysql> CREATE USER 사용자ID@localhost IDENTIFIED BY '비밀번호';
```
먼저 사용할 사용자를 추가해준다. [사용자ID] 부분에 원하는 사용자ID를 입력해주면 된다.

```
mysql> CREATE DATABASE 생성할 데이터베이스명;   //DB 생성
mysql> SHOW DATABASES;   //생성한 DB 확인
```
그 다음 사용할 데이터베이스를 생성해주고 잘 생성되었는지 확인한다.


```
mysql> GRANT ALL privileges ON 데이터베이스명.* TO 사용자ID@localhost;   //추가한 사용자에게 DB 권한 주기
```
사용자에게 생성한 DB의 권한을 준다.


### ✔ 테이블 생성

```
mysql> EXIT;
mysql> mysql -u student -p   //student 사용자로 접속
mysql> use userinfo   //생성한 DB 사용
```
사용자 추가와 데이터베이스 생성이 완료되었다면, root에서 나와서 추가한 사용자로 재접속을 해준다. <br>

<script src="https://gist.github.com/YounJ00/5172f2ff424693039afca5d0477a6474.js"></script>
마지막으로 로그인에 필요한 데이터들을 생성해준다.<br>
- id
- username
- password
- ...


## 2. 필요 모듈 설치

### ✔ 리액트 설치
```
npx create-react-app [프로젝트 명]
```
위 명령어로 리액트 프로젝트를 생성한다.

- mysql
- express
- express-session
- express-mysql-session
- body-parser
- bcrypt (비밀번호를 해시 암호화 해줌)

위 필요한 모듈들을 npm을 이용하여 다운로드 해준다.

```
npm install express
npm install express-session
npm install express-mysql-session
npm install mysql2
npm install bcrypt
npm install body-parser
```

### ✔ 파일 생성 및 정리

<img width="185" alt="image" src="https://github.com/YounJ00/YounJ00.github.io/assets/91127380/c7b95414-c6c4-4db8-b5db-dc31fbde4da9">

위는 기존 파일의 모습이다.
여기서 개발에 필요한 폴더 및 파일을 생성해준다.

<b>📂 생성 폴더 및 파일 📂</b>
- lib 폴더
- lib/db.js 파일
- lib/sessionOption.js
- server.js 파일

<img width="190" alt="image" src="https://github.com/YounJ00/YounJ00.github.io/assets/91127380/56694a1b-0d6a-44d4-b851-0cb9c9b97c34">


위처럼 빨간펜 부분을 만들어주면 된다.

## 3. 구현

### ✔ server.js

<script src="https://gist.github.com/YounJ00/5e90f3aea485d4a209e6070a0ae9364e.js"></script>

### ✔ App.js

<script src="https://gist.github.com/YounJ00/4ec42144ae555dc76ae5464484b19207.js"></script>

### ✔ App.css

<script src="https://gist.github.com/YounJ00/a64a76705ab4cd816867c678a5ed95f4.js"></script>

### ✔ db.js

<script src="https://gist.github.com/YounJ00/7d7aa9fa2fa4f7f272d243061a7cae4b.js"></script>

### ✔ sessionOption.js

<script src="https://gist.github.com/YounJ00/6a5f5c1886b9b7caf46fd7bb1b94aad9.js"></script>

## 4. 실행

<img width="370" alt="실행 gif" src="https://github.com/YounJ00/YounJ00.github.io/assets/91127380/72a0d4a7-05b7-4c64-b0a6-bb4cffbd90d5">

완성!!😊