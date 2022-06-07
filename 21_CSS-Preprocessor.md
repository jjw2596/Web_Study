# 💻 CSS 전처리기

## 📖 CSS 전처리기란?

> 전처리기 자신만의 특별한 syntax를 가지고 CSS를 생성하도록 하는 프로그램

* CSS의 문제점을 Programmatically 한 방식
* 변수, 함수, 상속 등 일반적인 프로그래밍 개념을 사용 가능
* CSS를 확장하기 위한 스크립팅 언어로 컴파일러를 통해 CSS 포맷으로 변환

<br>

## 📖 CSS 전처리기 모듈

* Sass/SCSS
* less
* Stylus
* PostCSS

<br>

* 서로의 특징에 맞게 약간의 syntaxㅁ나 다를뿐 개념 자체는 동일  
[CSS 전처리기 성능 비교 사이트](https://csspre.com/compile/)

<br>

### 장점

1. 재사용성
    * 공통 요소 또는 반복적인 항목을 변수, 함수로 대체 가능
2. 시간적 비용 감소
    * 임의 함수 및 내장 함수로 인한 개발 시간적 비용 절약
3. 유지 관리
    * CSS코드를 여러 파일로 나눠 유지 보수성 향상
    * 중첩, 상속과 같은 요소로 인해 구조화된 코드로 유지 및 관리 용이

### 단점

1. 전처리기를 위한 도구 필요
2. 개발에 대한 역할과 요소 접목으로 퍼블리셔나 디자이너가 개발적인 요소를 알아야 함  
   => 개발자에 한해서만 Learning curve 낮음

<br>

## 📖 사용 방법

1. 전처리기로 코딩  
    => 선택자의 중첩, 조건문, 반복문, 단위 등 기능 사용해 편리하게 작성
2. 표준 CSS로 컴파일  
    => 웹에서 직접 동작하지 않으므로 작성한 전처리기를 웹에서 동작가능한 표준의 CSS로 컴파일

### 컴파일 방법

* Sass
    ```
    sass style.scss style.css
    ```
* Less
    ```
    lessc style.less style.css
    ```
* Stylus
    ```
    stylus style.styl style.css
    ```
<br><br>

## 📖 Sass/SCSS 

![sass/scss](https://velog.velcdn.com/images%2Feunoia%2Fpost%2Fbb4ee5ae-66b2-4844-a319-73b581920395%2Fimage.png)

* 2006년부터 시작해 가장 오래된 CSS 확장 언어
* 기초 언어의 힘과 우아함을 더해주는 CSS 확장 언어

### Sass/SCSS 차이점

* Sass(Syntactically Awesom Style Sheets)의 version3에서 SCSS 등장
* SCSS와 CSS 구문은 완전히 호환되도록 새로운 구문을 도입해 만든 Sass의 모든 기능 지원  
    => SCSS가 CSS와 거의 같은 문법으로 Sass기능 지원

<br><br>

### Nesting

> 부모요소를 반복적으로 기술하지 않고 사용이 가능

```scss
// CSS
.header{
  width: 100%;
}
.header div{
  height: 100%;
}
.header div:hover{
  margin: 10%;
}
ㅤ
// SCSS
.header{
  width: 100%;
  div{
    height: 100%;
    &:hover{
      margin: 10%;
    }
  }
}
```

<br>

### $변수

> $를 사용해 공통된 속성들을 변수로서 재활용 할 수 있다.

```scss
$header-color: #d9d9d9;
ㅤ
.header{
  color: $header-color;
}
```

<br>

### @mixin

> @mixin을 사용해 공통된 속성의 <b>묶음</b>을 재활용할 수 있다.

```scss
@mixin header-style{
  width: 100%;
  height: 100%;
}
ㅤ
.header{
  @include header-style;
}
```

<br>

### @import

> @import를 통해 CSS파일을 가져올 수 있다.

```scss
@import 'header.scss'
```

<br>

### @if

> 조건 분기가 가능하다.

```scss
$theme: wave;
ㅤ
header{
  @if $theme == wave{
    color: blue;
  } @else if $theme == grass{
    color: green;
  } @else {
    color: white;
  }
}
```

<br>

### @for

> 반복문 사용이 가능하다.

```scss
@for $i from 0 through 3{
  .block-#{$i}{
    width: 30% * $i;
  }
}
```