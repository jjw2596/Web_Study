# 반응형 디자인과 미디어 쿼리 

## 반응형 디자인

### 반응형 디자인이란?  

* 사용자가 대상에 어떤 조작을 가할 때 그것의 상태나 모습이 변화하는 디자인을 뜻한다.

* 웹 사이트의 경우 사용자의 디바이스가 다양하기 때문에 디바이스, 창, 화면 크기 등에서 가장 최적의 배치로 보일 수 있도록 만드는 것이 사용자의 사용성과 기능성 측면에서 중요하다.

![responsive](https://velog.velcdn.com/images%2Fm-vault%2Fpost%2Fbb461ab6-b7a7-4837-a766-ac356bc20026%2F1.png)  

<br>

## 미디어 쿼리  

* 미디어 쿼리는 다양한 기기 특성과 parameter의 존재 여부에 따라 사이트, 또는 앱을 조정할 수 있다.
* 미디어 쿼리는 반응형 디자인의 핵심 구성요소이다.
* 기본적인 미디어 쿼리의 구문은 다음과 같다.
    ```css
    @media media-type and (media-feature-rule) {
    /* CSS rules go here */
    }
    ```

### 미디어 쿼리 구문의 구성요소
  * 어떤 미디어를 위한 것인지 브라우저에 알려주는 미디어 유형(인쇄 또는 화면)
  * 괄호로 묶은 CSS 규칙이 적용되기 위해 전달되어야 하는 규칙 또는 조건문경의 미디어 표현식
  * 조건문을 통과하고 미디어 유형이 올바른 경우 적용되는 CSS 규칙 집합

<br>

### 지정할 수 있는 미디어 유형
  * all
  * print
  * screen
  * speech

<br>

### 미디어 기능 규칙

* 미디어 유형을 지정한 후 규칙을 적용할 미디어 기능을 선택할 수 있음

1. 너비와 높이  
    ```min-width max-width width``` 등 미디어 기능을 활용하여 뷰포트가 특정 너비 이상 혹은 이하인 경우 CSS를 적용할 수 있다.
    ```css
    @media screen and (width: 600px) {
        body {
            color: red;
        }
    }
    ```
    -> 뷰포트가 정확히 600px인 경우 body의 글씨 색상을 red로 변경

2. 방향성 
    ```orientation```으로 세로 모드인지 가로 모드인지를 확인할 수 있다.
    ```css
    @media (orientation: landscape) {
        body {
            color: purple;
        }
    }
    ```
    -> 디바이스가 가로모드인 경우 body의 글씨 색상을 purple로 변경

3. 포인팅 장치의 사용 
    요소 위에 마우스가 올려진 상태, ```hover```인지 아닌지 확인할 수 있다.  
    ```css
    @media (hover: hover) {
        body {
            color: yellow;
        }
    }
    ```
    -> hover 상태인 경우 body에 있는 글씨 색상을 yellow로 변경

<br>

### '논리 곱' 미디어 쿼리

* ```and```를 사용해 미디어 기능을 결합할 수 있다.
    ```css
    @media screen and (min-width: 400px) and (orientation: landscape) {
        body {
            color: blue;
        }
    }
    ```
    -> 뷰포트 너비가 최소 400px 이상이고 장치가 가로모드인 경우 body의 글씨 색상을 blue로 변경

### '논리 합' 미디어 쿼리

* 논리 합 쿼리들은 콤마 ```,```로 분리할 수 있다.
    ```css
    @media screen and (min-width: 400px), screen and (orientation: landscape) {
        body {
            color: blue;
        }
    }
    ```
    -> 뷰포트 너비가 최소 400px 이상이거나 장치가 가로보드인 경우 body의 글씨 색상을 blue로 변경

### '부정 논리' 미디어 쿼리

* ```not``` 연산자를 사용하여 전체 미디어 쿼리를 부정할 수도 있다.
* 이 경우 적용한 미디어 쿼리의 전체 의미를 반대로 뒤집는다.
    ```css
    @media not all and (orientation: landscape) {
        body {
            color: blue;
        }
    }
    ```
    -> 가로모드가 아닐 때 즉, 디바이스가 세로 모드일 때 body의 글씨 색상을 blue로 변경