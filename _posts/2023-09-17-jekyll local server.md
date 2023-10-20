---
title: "jekyll 로컬 서버에서 실행"
author: cotes
date: 2023-09-17 11:33:00 +0800
categories: [Git 🌱, Blog]
tags: [GitBlog]
pin: true
math: true
mermaid: true
image:
  path: /assets/img/github.jpg
---

## 1. Ruby 설치

[Ruby Download Link](https://rubyinstaller.org/downloads/) 여기서 ruby를 설치해준다.

![1](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/456b3cbb-437c-4c4c-80b2-0a184a419c5f)

나는 제일 위에 있는 <b>Ruby+Devkit 3.2.2-1 (x64)</b> 를 다운받아주었다.

![2](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/32fbd6ac-76e3-4283-939d-bc0f02f55351)
rudy installer를 실행하면 위 사진과 같은 cmd창이 뜨는데, 1번(기본설치)를 누르고 엔터를 눌러 설치를 완료해줍니다.

## 2.  install jekyll

깃 블로그가 있는 디렉토리에서 git bash 창을 켜고
아래 명령어로 jekyll를 설치해준다.

```
$ gem install jekyll
```
![3](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/ff5b943e-22b6-4eaa-8ea7-11ffeb04b313)


## 3. bundler 설치

깃 블로그가 있는 디렉토리에서 cmd를 열어준다.<br>
그 다음 아래 명령어를 입력하여 bundler를 설치해준다.
```
install bundler
```

## 4. jekyll 로컬 서버 실행
![4](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/0d390576-c5de-4c9f-a233-331964fe60ba)

위와 같은 오류가 떴다면 깃 블로그 폴더에서 <b>Gemfile.lock</b> 파일을 삭제한 뒤, 아래 명령어를 통해 bundler를 update 해준다.
```
bundler update
```

그 다음 <b>bundle exec jekyll serve</b> 명령어를 통해 로컬 서버를 실행시킵니다.
```
bundle exec jekyll serve 
```

그러면 <b>http://127.0.0.1:4000/</b>에 접속하여 블로그를 확인할 수 있습니다!!

![5](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/33ad9e42-d635-4720-8c97-60a4f2e9d0c3)