---
title: "[빅데이터응용] 웹 크롤링"
author: cotes
date: 2023-09-23 11:33:00 +0800
categories: [Lecture 📚, 빅데이터응용]
tags: [빅데이터응용]
pin: true
math: true
mermaid: true
image:
---


<br>
빅데이터응용 수업 4주차 웹 크롤링 실습


## <span style="font-family:'GowunDodum-Regular'; font-weight:900; color:#3b5998;">필요 라이브러리 설치</span>

크롤링을 하기 위해서는 **selenium, bs4, tqdm** 라이브러리를 설치해줘야한다.
```
!pip install selenium
!pip install bs4
!pip install tqdm
```
**🖇 Selenium**<br>
- 웹 애플리케이션을 자동으로 테스트하고 웹 브라우징을 자동화하기 위한 파이썬 라이브러리이다.<br>
- 웹 브라우저를 제어하여 웹 페이지를 열고, 클릭하고, 양식을 작성하고, 데이터를 추출하는 등 다양한 웹 액션을 자동으로 수행할 수 있다.

**🖇 BeautifulSoup (bs4)**
- HTML 및 XML 문서를 파싱하고 검색하고 데이터를 추출하기 위한 파이썬 라이브러리이다.
- 웹 크롤링 시에 HTML 페이지의 내용을 추출하고 분석하는 데 사용된다.

**🖇 tqdm**
- "진행 상황 바"를 제공하여 반복 작업의 진행 상황을 시각적으로 표시하는 데 사용되는 라이브러리이다.
- 반복문 내에서 진행 중인 작업에 대한 진행률 표시, 예상 시간 남은 시간 등을 제공하여 사용자에게 작업의 진행 상황을 알려준다.

## <span style="font-family:'GowunDodum-Regular'; font-weight:900; color:#3b5998;">웹 크롤링 (crawling)</span>
### ✔ 크롤링 할 사이트
<b>[common sense media](https://www.commonsensemedia.org/)</b> > Movies > Best Movie Lists > Latin American Academy Award Winners and Nomineess


![1](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/f5a4c9bb-be39-448a-b73e-ae9bc79ad9ef)

### ✔ 실습

<script src="https://gist.github.com/YounJ00/957c2b5462da38dce0d6bcf59a887ae0.js"></script>

위 코드는 **Selenium 및 BeautifulSoup (bs4) 라이브러리**를 사용하여 웹 페이지를 열고 원하는 데이터를 추출하거나 웹 애플리케이션을 자동으로 조작하기 위한 코드이다.

-----------------------------------------------
<script src="https://gist.github.com/YounJ00/90e3f03d40b742214a1bb464eb629982.js"></script>

**webdriver.Chrome()**을 통해 Chrome 웹 드라이버를 초기화해주고, 크롤링 할 웹 URL 을 'start_url'에 저장해준다.<br>
그리고 **driver.get(start_url)**을 통해 웹 브라우저를 열고 지정된 URL을 로드해준다.

-----------------------------------------------
<script src="https://gist.github.com/YounJ00/02ecf62f2c16220e469d418728402657.js"></script>

위 코드는 웹 페이지를 **스크롤 다운하는 함수인 scroll_down**을 정의하고 호출한다.<br>
웹 페이지의 끝에 도달할 때까지 스크롤 다운하는 기능을 제공하며, 스크롤 다운 동작이 너무 빠르지 않게 조절하여 원하는 정보를 모두 수집하기 위해 사용될 수 있습니다.

-----------------------------------------------
<script src="https://gist.github.com/YounJ00/d7e4693615f1113ab5c7e43daeae929b.js"></script>

![2](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/f54ea157-9886-4d20-ac4e-5071204be596)

그냥 soup을 출력하게 되면 위처럼 페이지의 **전체 html 소스**를 가져온다.<br>
그래서 **find_all()함수**를 사용하여 **특정 태그의 html 소스**를 받아온다.<br>

나는 영화 제목을 가져오고 싶기 때문에 영화 제목에서 검사를 해주었다.

![3](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/d4b2eb47-6a80-4412-bd10-00e00e2f8aa8)

### ✔ 원하는 값의 element 복사
**복사 경로 : 내가 가져오고 싶은 값 우클릭 > 검사 > 선택된 html 소스 우클릭 > Copy > Copy element**

<span style="font-family:'GowunDodum-Regular'; font-weight:900; color:#804da1;">[복사한 element]</span>

```html
<h3 class="review-title">
      <a class="link link--title" href="/movie-reviews/encanto">Encanto</a>
</h3>
```
위에 복사된 element 를 보면 **class가 "review-title" 인 h3** 태그에 영화 제목이 들어가 있는 것을 확인할 수 있다.

![4](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/cc5bc068-ea29-4c23-9a10-50c50742ad17)

-----------------------------------------------
하지만 우리는 영화 제목이 있는 태그의 html 소스를 가져오기 보다는 영화 제목만을 가져와야하기 때문에 **h3 > a 태그의 텍스트**를 찾아야 한다.<br>

그렇기 때문에 **find('a') 함수**를 통해 다시 한 번 a태그를 찾아준 다음에, **a태그의 text 만**을 뽑아서 출력해준다.

<script src="https://gist.github.com/YounJ00/fdad31cee70da8b75357ab8e4b62d385.js"></script>

<img width="550" alt="" src="https://github.com/YounJ00/YounJ00.github.io/assets/91127380/5de2530b-2b45-4240-93a4-adc8f1c927dd">

-----------------------------------------------
크롤링을 통해 받아온 데이터를 **list**에 추가하여 출력해줄 수 있다.
<script src="https://gist.github.com/YounJ00/7c8a3cf24849e86ca7e92bfcbf58d677.js"></script>

![6](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/a4acffab-c3c9-4761-8c6e-b52c1a4c57c6)

## <span style="font-family:'GowunDodum-Regular'; font-weight:900; color:#3b5998;">동적 크롤링</span>
### ✔ 원하는 button의 XPath 복사
복사 경로 : 이동을 원하는 버튼 우클릭 > 검사 > 코드 우클릭 > Copy > **Copy XPath**
<br>

![7](https://github.com/YounJ00/YounJ00.github.io/assets/91127380/6d6d1f6e-b606-4c7c-aa82-0e7cefbf2404)

**[복사한 XPath] :** <span style="font-family:'GowunDodum-Regular'; font-weight:900; color:#804da1;">//*[@id="review-teaser-82065"]/div[3]/a</span>
```python
driver.find_element(By.XPATH, r'//*[복사한 XPath]').click()
```

<script src="https://gist.github.com/YounJ00/c77e6091be4b1d6b1b017debdaeaf47a.js"></script>

<img width="550" alt="" src="https://github.com/YounJ00/YounJ00.github.io/assets/91127380/4aae7c1e-2dc3-42ef-a227-1eed3c3960eb">
