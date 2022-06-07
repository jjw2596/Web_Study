# 💻 CSS 구조(Architecture)

## 💻 BEM

## 📖 BEM이란?

> BEM은 Block, Element, Modifier를 뜻한다. 저 세 가지로 구성된 이름을 짓는 것을 의미하며 각각 __와 --로 구분한다.

## 📖 BEM 구조

```css
.header__navigation--navi-text {
    color: red;
}
```

* 위 코드에서 header는 `Block`, navigation은 `Element`, navi-text는 `Modifier`가 된다.
* BEM은 기본적으로 ID를 사용하지 않으며 class만을 사용
* '어떻게 보이는가'가 아니라 <b>'어떤 목적인가'</b>에 따라 이름을 짓는다.

<br><br>

## 📖 Block

* 재사용 가능한 기능적으로 독립적인 페이지 컴포넌트(A functionally independent page component that can be reused)를 블럭이라고 부른다.
* ex) Logo 블럭은 어딘가에 종속되지 않는다. 헤더에 쓰일 수도 있고, footer에 쓰일 수도 있고 여기저기 붙였다 떼었다 할 수 있다.
* 이렇게 재사용할 수 있는 요소를 블럭이라고 한다. 

<br><br>

## 📖 Element

* 엘리먼트는 블럭을 구성하는 단위이다.
* 블럭은 독립적인 형태인 반면, 엘리먼트는 의존적인 형태
* 자신이 속한 블럭 내에서만 의미를 가지기 때문에 블럭 안에서 떼어다 다른데 쓸 수 없다.
```html
<form class="search-form">
    <input class="search-form__input"/>
    <button class="search-form__button">Search</button>
</form>
```
* 위 예시에서 .search-form은 블럭이고, .search-form 뒤의 `__input`과 `__button`은 엘리먼트이다.
* search-form이란 블럭은 다른 곳에서 재사용이 가능
* But, `__input`과 `__button`은 search-form 안에서만 존재 의미가 있는 엘리먼트이다.
* 엘리먼트 또한 중첩이 가능 : block > .block__element1 > .block__element2 같은 형태가 가능
* 그러나 .block__element2를 .block__element1의 하위 엘리먼트로 보지 않고, 똑같은 .block의 엘리먼트로 취급
* BEM의 잘못된 예시
    ```html
    <form class="search-form">
        <div class="search-form__content">
            <input class="search-form__content__input"/>
            <button class="search-form__content__button">Search</button>
        </div>
    </form>
    ```
* BEM의 올바른 예시
    ```html
    <form class="search-form">
        <div class="search-form__content">
            <input class="search-form__input"/>
            <button class="search-form__button">Search</button>
        </div>
    </form>
    ```

<br><br>

## 📖 Modifier

* modifier는 블럭이나 엘리먼트의 속성을 담당
* 생긴게 조금 다르거나, 다르게 동작하는 블럭이나 엘리먼트를 만들 때 사용
### Boolean 타입

* 아래 코드에서 --focused가 수식에 해당. boolean은 그 값이 true라고 가정하고 사용
    ```html
    <ul class="tab">
        <li class="tab__item tab__item--focused">탭 01</li>
        <li class="tab__item">탭 02</li>
        <li class="tab__item">탭 03</li>
    </ul>
    ```

### Key-Value 타입

* key-value 타입은 하이픈으로 `성질-내용`을 작성
* 아래 예시에서 color-gray와 theme-normal이 `key-value` 타입에 해당
    ```html
    <div class="column">
        <strong class="title">일반 로그인</strong>
        <form class="form-login form-login--theme-normal">
            <input type="text" class="form-login__id"/>
            <input type="password" class="form-login__password"/>
        </form>
    </div>
    
    <div class="column">
        <strong class="title title--color-gray">VIP 로그인 (준비중)</strong>
        <form class="form-login form-login--theme-special form-login--disabled">
            <input type="text" class="form-login__id"/>
            <input type="password" class="form-login__password"/>
        </form>
    </div>
    ```

<br><br>

## 📖 BEM의 장점과 단점

### 장점

1. 클래스 네임만으로 마크업 구조를 알 수 있다.
    * 블럭과 엘리먼트로 구분되기 때문에 어디서부터 떼어 쓸 수 있는지, 어디서부터 종속되는지 알 수 있다.
2. SASS의 부모참조자(&)와 함께 쓰기 편하다.
3. 작성된 SASS에서 요소를 쉽게 찾을 수 있다.
4. SASS 작성 시, 늘어지는 셀렉팅을 막아준다.
    * 기존의 nested 방식으로 SASS를 작성하면, 컴파이 시 셀렉팅이 끝도 없이 길어지는 경우가 있으나 BEM 방식을 쓰면 너도나도 엘리먼트라서 굳이 깊게 nested할 필요가 없어진다.

### 단점

1. 클래스 네임이 너무 길다.
2. 더블클릭 선택이 불편하다.