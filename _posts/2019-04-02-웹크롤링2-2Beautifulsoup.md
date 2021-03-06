---
title: "웹 크롤링_BeautifulSoup"
header:
 overlay_image: /assets/images/overlayimage.jpg
categories:
  - crawling
tags:
  - BeautifulSoup
  - urljoin
toc: true
toc_label: "페이지 주요 목차"
toc_sticky: true
---
웹 크롤링 문법  
직접접근, 태그로 접근, CSS선택자로 접근, 정규표현식

# urljoin
```python
from urllib.parse import urljoin
baseUrl = "https://test.com/html/a.html"
print(">>", urljoin(baseUrl,"b.html"))
    #결과: >> https://test.com/html/b.html
print(">>", urljoin(baseUrl,"sub/b.html"))
    #결과: >> https://test.com/html/sub/b.html
print(">>", urljoin(baseUrl,"../index.html"))
    #결과: >> https://test.com/b.html
print(">>", urljoin(baseUrl,"../img/img.jpg"))
    #결과: >> https://test.com/img/img.jpg
```

# BeautifulSoup
1. 직접접근 방식
2. 태그로 접근 방식
3. CSS 선택자로 접근 방식

## 직접접근 방식 ; soup.html.h1,p
```html
<html><body>
  <h1>파이썬 BeautifulSoup 공부</h1>
  <p>태그 선택자</p>
  <p>CSS 선택자</p>
</body></html>
```
```python
soup = BeautifulSoup(html, 'html.parser')
print(type(soup))
    #결과: <class 'bs4.BeautifulSoup'>
#""직접 접근하자""
h1  = soup.html.body.h1
p_1 = soup.html.body.p
p_2 = soup.html.body.p.next_sibling
p_3 = soup.html.body.p.next_sibling.next_sibling
p_4 = soup.html.body.p.previous_sibling.previous_sibling
print(type(h1))
    #결과: <class 'bs4.element.Tag'> class형태임, 그리고 Tag라는 객체를 갖고왔다.
print(h1)
    #결과: <h1>파이썬 BeautifulSoup 공부</h1>
print(h1.string)
    #결과: 파이썬 BeautifulSoup 공부
print(p_1)
    #결과: <p>태그 선택자</p> 첫번째 태그 갖고왔다.
print(p_2)
    #결과: 아무것도 없음, 그 이유는 <p>태그 선택자</p>[줄바꿈키]<p>CSS 선택자</p> 중간에 줄바꿈키 때문에 줄바꿈 키를 찾았기 때문이다.
print(p_3)
    #결과: <p>CSS 선택자</p>
print(p_4)
    #결과: <h1>파이썬 BeautifulSoup 공부</h1>
```
    그러나 next_sibling previous_sibling는 계속 크롤링 할때는 사용하지 않는다. 왜냐면 사이트가 수정되면 다른 값이 나오기 때문이다.


## 태그로 접근 방식 : find, find_all
- find() : 가장 먼저 검색되는 태그 반환
- find_all() : 전체 태그 반환
```html
<html><body>
  <ul>
    <li><a href="http://www.naver.com">naver</a></li>
    <li><a href="http://www.daum.net">daum</a></li>
    <li><a href="https://www.google.com">google</a></li>
    <li><a href="https://www.tistory.com">tistory</a></li>
  </ul>
</body></html>
```
```python
soup = BeautifulSoup(html, 'html.parser')
links_1 = soup.find_all("a") #a태그를 link변수에 한방에 모두 담는다.
print(type(links_1))
    #결과: <class 'bs4.element.ResultSet'>
print(links_1)
    #결과: [<a href="http://www.naver.com">naver</a>, <a href="http://www.daum.net">daum</a>, <a href="https://www.google.com">google</a>, <a href="https://www.tistory.com">tistory</a>]

for a in links_1:
  print(type(a), a)
    #결과: <class 'bs4.element.Tag'> <a href="http://www.naver.com">naver</a>
    #결과: <class 'bs4.element.Tag'> <a href="http://www.daum.net">daum</a>
    #결과: <class 'bs4.element.Tag'> <a href="https://www.google.com">google</a>
    #결과: <class 'bs4.element.Tag'> <a href="https://www.tistory.com">tistory</a>
  print(a.string)
    #결과: naver
  print(a.attrs['href'])
    #결과: http://www.naver.com, .....

links_2 = soup.find_all("a", string="daum")
    #결과: [<a href="http://www.daum.net">daum</a>]
links_3 = soup.find_all("a", limit=3)
    #결과: [<a href="http://www.naver.com">naver</a>, <a href="http://www.daum.net">daum</a>, <a href="https://www.google.com">google</a>]
links_4 = soup.find_all(sting=["naver","google"])
    #결과: ['naver', 'google']
```
    links_1 = soup.find_all("a") #처럼 모든 a태그를 link변수에 담는데 이는 실전에서 너무 복잡할 수 있다.  


## CSS 선택자로 접근 방식 : select_one, select
```html
<html><body>
<div id="main">
  <h1>강의목록</h1>
  <ul class="lecs">
    <li>Java 초고수 되기</li>
    <li>파이썬 기초 프로그래밍</li>
    <li>파이썬 머신러닝 프로그래밍</li>
    <li>안드로이드 블루투스 프로그래밍</li>
  </ul>
</div>
</body></html>
```
```python
soup = BeautifulSoup(html, 'html.parser')

#soup.select()
h1 = soup.select("div#main > h1")
print(type(h1))
    #결과: <class 'list'>
print(type(h1), h1)
    #결과: [<h1>강의목록</h1>]
print(h1[0].string)
    #결과: 강의목록
for z in h1:
  print(z.string)
    #결과: 강의목록

#soup.select_one()
h1_1 = soup.select_one("div#main > h1")
print(type(h1_1))
    #결과: <class 'bs4.element.Tag'>
print(h1_1)
    #결과: <h1>강의목록</h1> , 위에 select()는 list 형태이다.
print(h1_1.string)
    #결과: 강의목록

#soup.select()
list_li = soup.select("div#main > ul.lecs > li")
for li in list_li:
  print(li.string)
    #결과: Java 초고수 되기
    #결과: 파이썬 기초 프로그래밍
    #결과: 파이썬 머신러닝 프로그래밍
    #결과: 안드로이드 블루투스 프로그래밍
```
    둘의 차이점은 갖고올게 한개라면 select_one을 사용하고, 아니면 select사용

# 정규표현식
## 정규표현식으로 find, find_all 이용
```html
<html><body>
  <ul>
    <li><a id="naver" href="http://www.naver.com">naver</a></li>
    <li><a href="http://www.daum.net">daum</a></li>
    <li><a href="http://www.daum.com">daum</a></li>
    <li><a href="https://www.google.com">google</a></li>
    <li><a href="https://www.tistory.com">tistory</a></li>
  </ul>
</body></html>
```
```python
soup = BeautifulSoup(html, 'html.parser')
print(soup.find(id = "naver").string) #id값으로 바로 찾기.
    #결과값: naver
#정규식으로 내가 원하는 조건으로 검색할 수 있다.
import re

li = soup.find_all(href=re.compile(r"^https://"))
print(li) #결과값: [<a href="https://www.google.com">google</a>, <a href="https://www.tistory.com">tistory</a>]
for e in li:
    print(e.attrs['href'])
        #결과값: https://www.google.com
        #결과값: https://www.tistory.com
li = soup.find_all(href=re.compile(r"da"))
for e in li:
    print(e.attrs['href'])
        #결과값: http://www.daum.net
        #결과값: http://www.daum.com

```
## 정규표현식으로 select, select_all 이용
```html
<div id="foods">
  <h1>안주 및 주류</h1>
  <ul id="fd-list">
    <li class="food hot" data-lo="ko">닭도리탕</li>
    <li class="food" data-lo="jp">돈까스</li>
    <li class="food hot" data-lo="ko">삼겹살</li>
    <li class="food" data-lo="us">스테이크</li>
  </ul>
  <ul id="ac-list">
    <li class="alcohol" data-lo="ko">소주</li>
    <li class="alcohol" data-lo="us">맥주</li>
    <li class="alcohol" data-lo="ko">막걸리</li>
    <li class="alcohol high" data-lo="cn">양주</li>
    <li class="alcohol" data-lo="ko">동동주</li>
  </ul>
</div>
```
```python
from bs4 import BeautifulSoup

fp = open("food-list.html", encoding="utf-8")
soup = BeautifulSoup(fp, "html.parser")

#정규 표현식을 이용해서 CSS선택자로 다양한 예제로 뽑을수 있다.
##select_one
print("1", soup.select_one("li:nth-of-type(1)").string)
print("2", soup.select_one("#ac-list > li:nth-of-type(4)").string)
##select
print("3", soup.select("#ac-list > li[data-lo='cn']")[0].string) #select는 list형태로 반환한다.
print("4", soup.select("#ac-list > li.alcohol.high")[0].string)
print("44", soup.select("#ac-list > li[class='alcohol']")[1].string) #select는 list형태로 반환한다.
#find
param = {"data-lo":"cn", "class":"alcohol"}
print("5", soup.find("li",param).string)
print("6", soup.find(id="ac-list").find("li",param).string)
#find_all
for ac in soup.find_all("li"):
    if ac['data-lo'] == 'us':
        print('data-lo == us', ac.string)

```
## 함수를 사용하여 select_one 이용
```html
<ul id="cars">
  <li id="ge">Genesis</li>
  <li id="av">Avante</li>
  <li id="so">Sonata</li>
  <li id="gr">Grandeur</li>
  <li id="tu">Tucson</li>
</ul>
```
```python
from bs4 import BeautifulSoup

fp = open("cars.html", encoding="utf-8")
soup = BeautifulSoup(fp, "html.parser")

def car_func(selector):
    print("car_func", soup.select_one(selector).string)

car_func("#gr")
car_func("li#gr")
car_func("ul > li#gr")
car_func("#cars #gr")
car_func("#cars > #gr")
car_func("li[id=gr]")

print("car_func",soup.select("li")[3].string)
print("car_func",soup.find_all("li")[3].string)
```
