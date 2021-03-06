# 레이아웃 만들기  

* 레이아웃은 특정 공간에 여러 구성 요소를 효과적으로 배치하는 것을 말한다.

## Floats

* float 속성은 해당 HTML 요소가 주변의 다른 요소들과 자연스럽게 어울리도록 만들어 준다.
* 이 속성은 본래 text 속성과 img 속성을 배치할 때 등 사용하는 목적으로 만들어졌지만, 현재는 웹 페이지의 레이아웃(layout)을 작성할 때 자주 사용된다.

    * inherit: 부모 요소에서 상속
    * left: 왼쪽에 부유하는 블록 박스를 생성.
    * right: 오른쪽에 부유하는 블록 박스를 생성. 페이지 내용은 박스 왼쪽에 위치하며 위에서 아래로 흐름. 이후 요소에 clear 속성이 있으면 페이지 흐름이 달라짐.
    * none: 요소를 부유시키지 않음
* left와 right를 통해 속성을 지정시 display는 무시된다(none은 제외). 또한 이후 요소에 clear 속성이 있으면 페이지 흐름이 달라진다.
<br>

## Positioning

* position 속성은 태그를 어떻게 위치시킬지를 정의하며, 아래의 5가지 값을 갖는다.
  * static: 기본값, 다른 태그와의 관계에 의해 자동으로 배치되며 위치를 임의로 설정해 줄 수 있다.
  * absolute: 절대 좌표와 함께 위치를 지정해 줄 수 있다.
  * relative: 원래 있던 위치를 기준으로 좌표를 지정한다.
  * fixed: 스크롤과 상관없이 항상 문서 최좌측상단을 기준으로 좌표를 고정한다.
  * inherit: 부모 태그의 속성 값을 상속받는다.

* 좌표를 지정 해주기 위해서는 left, right, top, bottom 속성과 함께 사용된다.
* position을 absolute나 fixed로 설정시 가로 크기가 100%가 되는 block 태그의 특징이 사라지게 된다.
* relative인 컨테이너 내부에 absolute인 객체가 있으면 절대 좌표를 계산할 때, relative 컨테이너를 기준점으로 잡게된다.(없다면 전체 문서가 기준)

<br>

## Display

* display 속성은 태그를 화면에 어떻게 드러나게 할 지를 결정하는 속성이다.

  * none: 화면에서 사라진다. 크기를 차지하지 않는다.
  * block: 기본값, 가로 한 줄을 다 차지한다.
  * inline: 컨텐츠를 딱 감쌀 정도의 크기만 갖는다. block태그와 달리 줄바꿈이 되지 않고, 크기를 변화시킬 수 없다.
  * inline-block: inline과 block의 특성을 합쳐놓은 속성이다. 기본적으로 inline의 속성을 가지지만, 임의로 크기를 바꿔줄 수 있다.

<br>

## CSS Grid  

* flex는 1차원 레이아웃 시스템이고 Grid는 2차원 시스템이다.
* Grid는 부모 요소인 Grid Container와, 자식요소인 Grid Item으로 구성되어 있다.
* 표와 같은 형태로 생겼지만 아이템의 구성과 배치가 간편하다.  
[CSS Grid](https://studiomeal.com/archives/533) < Grid 정리

<br>

## Flex Box  

* flexbox는 뷰포트나 요소의 크기가 불명확하거나 동적으로 변할 때에도 효율적으로 요소를 배치, 정렬, 분산할 수 있는 방법을 제공하는 CSS3의 새로운 레이아웃 방식이다.
* flexbox의 장점을 한 마디로 표현하면 '복잡한 계산 없이 요소의 크기와 순서를 유연하게 배치할 수 있다.'라고 할 수 있다.
* 정렬, 방향, 순서, 크기 등을 유연하게 조절할 수 있기 때문에 별도의 분기 처리를 줄일 수 있고, CSS만으로 다양한 레이아웃을 구현할 수 있다. 
* 부모 요소인 flex container와 자식 요소인 flex item으로 구성되어 있다.
[CSS Flex](https://studiomeal.com/archives/197) < Flex 정리

