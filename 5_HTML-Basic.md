# HTML - 기초 배우기


## HTML이란?

* HTML은 HyperText Markup Language의 약자로 웹 페이지를 위한 마크업 언어이다.
> 마크업 언어는 태그 등을 잉요하여 문서나 데이터의 구조를 명기하는 언어의 한 가지이다.
  
* 제목, 단락, 목록 등과 같은 본문을 위한 구조적 의미를 나타내며 링크, 인용, 그 밖의 항목으로 구조적 문서를 만들 수 있는 방법을 제공한다.

* 웹 페이지는 HTML 문서라고도 불리며, HTML 태그들로 구성된다.

![HTML5](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcBLDUV%2FbtrnBtzzzEt%2Fm0BsMSnKFE2hFW3KRtTA31%2Fimg.png)

## HTML의 형식

* HTML은 웹 페이지 콘텐츠 안의 꺽쇠(<>)로 둘러싸인 "**태그**"로 되어있는 HTML 요소 형태로 작성한다.  

* HTML은 웹 브라우저와 같은 HTML 처리 장치의 행동에 영향을 주는 **자바스크립트**와 본문과 그 밖의 항목의 외관과 배치를 정의하는 CSS 같은 스크립트를 포함하거나 불러올 수 있다.  

## HTML 태그

HTML을 구성하는 태그는 디자인이나 기능을 결정하는데 사용된다.
```html
<tag> //시작 태그
    내용
</tag> //종료 태그
```
태그에 따라 시작 태그만 있고 종료 태그가 없는 경우(img, br, hr 등)가 있지만 react에서는 종료 태그를 엄격하게 감시하므로 
```html
<tag />
```
시작태그 안에서 종료를 선언하기도 한다.  

[태그의 종류](http://www.tcpschool.com/html-tags/intro)

## HTML 버전

![HTMLVersion](https://media.vlpt.us/images/ezae/post/d01f053b-e89b-44c2-b53b-95ddd4e28f5d/image.png)

HTML 문서 작성시 첫 줄에 작성되는 DOCTYPE 선언 방식의 차이로 버전을 다르게 작성할 수 있으며 현재는 HTML5가 최신 버전이다.  