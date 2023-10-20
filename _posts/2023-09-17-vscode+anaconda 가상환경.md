---
title: "[빅데이터응용] VS Code + Anaconda 가상환경 구축"
author: cotes
date: 2023-09-17 11:33:00 +0800
categories: [Lecture 📚, 빅데이터응용]
tags: [빅데이터응용]
pin: true
math: true
mermaid: true
image:
---


<br>
visual studio에서 anaconda 가상환경 구축

## 1. visual studio 설치
## 2. anaconda 설치
## 3. 환경변수 -> 사용자변수 -> Path 편집 -> 아래 3개 경로 추가
- C:\Users\younjin\AppData\Local\anaconda3
- C:\Users\younjin\AppData\Local\anaconda3\Library\bin
- C:\Users\younjin\AppData\Local\anaconda3\Scripts

## 4. anaconda prompt 열기
## 5. 가상환경 만들기
   conda create --name bigdata python==3.9
## 6. 만든 가상환경으로 이동
   conda activate bigdata
## 7. pandas 설치
   pip install pandas
   확인 -> python -> import pandas as pd -> exit()

## 8. vs code -> open folder(파일 저장할 폴더) -> .ipynb 파일 생성

## 9. select kernel -> python environments -> bigdata(만든 가상환경)
안나오면 ctrl+shift+ P -> Python: select interpreter

## 10. 터미널 안들어가고 바로 작업하고싶다
-> !pip install matplotlib 해주면 된다.
shift+Enter