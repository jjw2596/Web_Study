# ๐ป CSS ๊ตฌ์กฐ(Architecture)

## ๐ป BEM

## ๐ BEM์ด๋?

> BEM์ Block, Element, Modifier๋ฅผ ๋ปํ๋ค. ์  ์ธ ๊ฐ์ง๋ก ๊ตฌ์ฑ๋ ์ด๋ฆ์ ์ง๋ ๊ฒ์ ์๋ฏธํ๋ฉฐ ๊ฐ๊ฐ __์ --๋ก ๊ตฌ๋ถํ๋ค.

## ๐ BEM ๊ตฌ์กฐ

```css
.header__navigation--navi-text {
    color: red;
}
```

* ์ ์ฝ๋์์ header๋ `Block`, navigation์ `Element`, navi-text๋ `Modifier`๊ฐ ๋๋ค.
* BEM์ ๊ธฐ๋ณธ์ ์ผ๋ก ID๋ฅผ ์ฌ์ฉํ์ง ์์ผ๋ฉฐ class๋ง์ ์ฌ์ฉ
* '์ด๋ป๊ฒ ๋ณด์ด๋๊ฐ'๊ฐ ์๋๋ผ <b>'์ด๋ค ๋ชฉ์ ์ธ๊ฐ'</b>์ ๋ฐ๋ผ ์ด๋ฆ์ ์ง๋๋ค.

<br><br>

## ๐ Block

* ์ฌ์ฌ์ฉ ๊ฐ๋ฅํ ๊ธฐ๋ฅ์ ์ผ๋ก ๋๋ฆฝ์ ์ธ ํ์ด์ง ์ปดํฌ๋ํธ(A functionally independent page component that can be reused)๋ฅผ ๋ธ๋ญ์ด๋ผ๊ณ  ๋ถ๋ฅธ๋ค.
* ex) Logo ๋ธ๋ญ์ ์ด๋๊ฐ์ ์ข์๋์ง ์๋๋ค. ํค๋์ ์ฐ์ผ ์๋ ์๊ณ , footer์ ์ฐ์ผ ์๋ ์๊ณ  ์ฌ๊ธฐ์ ๊ธฐ ๋ถ์๋ค ๋ผ์๋ค ํ  ์ ์๋ค.
* ์ด๋ ๊ฒ ์ฌ์ฌ์ฉํ  ์ ์๋ ์์๋ฅผ ๋ธ๋ญ์ด๋ผ๊ณ  ํ๋ค. 

<br><br>

## ๐ Element

* ์๋ฆฌ๋จผํธ๋ ๋ธ๋ญ์ ๊ตฌ์ฑํ๋ ๋จ์์ด๋ค.
* ๋ธ๋ญ์ ๋๋ฆฝ์ ์ธ ํํ์ธ ๋ฐ๋ฉด, ์๋ฆฌ๋จผํธ๋ ์์กด์ ์ธ ํํ
* ์์ ์ด ์ํ ๋ธ๋ญ ๋ด์์๋ง ์๋ฏธ๋ฅผ ๊ฐ์ง๊ธฐ ๋๋ฌธ์ ๋ธ๋ญ ์์์ ๋ผ์ด๋ค ๋ค๋ฅธ๋ฐ ์ธ ์ ์๋ค.
```html
<form class="search-form">
    <input class="search-form__input"/>
    <button class="search-form__button">Search</button>
</form>
```
* ์ ์์์์ .search-form์ ๋ธ๋ญ์ด๊ณ , .search-form ๋ค์ `__input`๊ณผ `__button`์ ์๋ฆฌ๋จผํธ์ด๋ค.
* search-form์ด๋ ๋ธ๋ญ์ ๋ค๋ฅธ ๊ณณ์์ ์ฌ์ฌ์ฉ์ด ๊ฐ๋ฅ
* But, `__input`๊ณผ `__button`์ search-form ์์์๋ง ์กด์ฌ ์๋ฏธ๊ฐ ์๋ ์๋ฆฌ๋จผํธ์ด๋ค.
* ์๋ฆฌ๋จผํธ ๋ํ ์ค์ฒฉ์ด ๊ฐ๋ฅ : block > .block__element1 > .block__element2 ๊ฐ์ ํํ๊ฐ ๊ฐ๋ฅ
* ๊ทธ๋ฌ๋ .block__element2๋ฅผ .block__element1์ ํ์ ์๋ฆฌ๋จผํธ๋ก ๋ณด์ง ์๊ณ , ๋๊ฐ์ .block์ ์๋ฆฌ๋จผํธ๋ก ์ทจ๊ธ
* BEM์ ์๋ชป๋ ์์
    ```html
    <form class="search-form">
        <div class="search-form__content">
            <input class="search-form__content__input"/>
            <button class="search-form__content__button">Search</button>
        </div>
    </form>
    ```
* BEM์ ์ฌ๋ฐ๋ฅธ ์์
    ```html
    <form class="search-form">
        <div class="search-form__content">
            <input class="search-form__input"/>
            <button class="search-form__button">Search</button>
        </div>
    </form>
    ```

<br><br>

## ๐ Modifier

* modifier๋ ๋ธ๋ญ์ด๋ ์๋ฆฌ๋จผํธ์ ์์ฑ์ ๋ด๋น
* ์๊ธด๊ฒ ์กฐ๊ธ ๋ค๋ฅด๊ฑฐ๋, ๋ค๋ฅด๊ฒ ๋์ํ๋ ๋ธ๋ญ์ด๋ ์๋ฆฌ๋จผํธ๋ฅผ ๋ง๋ค ๋ ์ฌ์ฉ
### Boolean ํ์

* ์๋ ์ฝ๋์์ --focused๊ฐ ์์์ ํด๋น. boolean์ ๊ทธ ๊ฐ์ด true๋ผ๊ณ  ๊ฐ์ ํ๊ณ  ์ฌ์ฉ
    ```html
    <ul class="tab">
        <li class="tab__item tab__item--focused">ํญ 01</li>
        <li class="tab__item">ํญ 02</li>
        <li class="tab__item">ํญ 03</li>
    </ul>
    ```

### Key-Value ํ์

* key-value ํ์์ ํ์ดํ์ผ๋ก `์ฑ์ง-๋ด์ฉ`์ ์์ฑ
* ์๋ ์์์์ color-gray์ theme-normal์ด `key-value` ํ์์ ํด๋น
    ```html
    <div class="column">
        <strong class="title">์ผ๋ฐ ๋ก๊ทธ์ธ</strong>
        <form class="form-login form-login--theme-normal">
            <input type="text" class="form-login__id"/>
            <input type="password" class="form-login__password"/>
        </form>
    </div>
    
    <div class="column">
        <strong class="title title--color-gray">VIP ๋ก๊ทธ์ธ (์ค๋น์ค)</strong>
        <form class="form-login form-login--theme-special form-login--disabled">
            <input type="text" class="form-login__id"/>
            <input type="password" class="form-login__password"/>
        </form>
    </div>
    ```

<br><br>

## ๐ BEM์ ์ฅ์ ๊ณผ ๋จ์ 

### ์ฅ์ 

1. ํด๋์ค ๋ค์๋ง์ผ๋ก ๋งํฌ์ ๊ตฌ์กฐ๋ฅผ ์ ์ ์๋ค.
    * ๋ธ๋ญ๊ณผ ์๋ฆฌ๋จผํธ๋ก ๊ตฌ๋ถ๋๊ธฐ ๋๋ฌธ์ ์ด๋์๋ถํฐ ๋ผ์ด ์ธ ์ ์๋์ง, ์ด๋์๋ถํฐ ์ข์๋๋์ง ์ ์ ์๋ค.
2. SASS์ ๋ถ๋ชจ์ฐธ์กฐ์(&)์ ํจ๊ป ์ฐ๊ธฐ ํธํ๋ค.
3. ์์ฑ๋ SASS์์ ์์๋ฅผ ์ฝ๊ฒ ์ฐพ์ ์ ์๋ค.
4. SASS ์์ฑ ์, ๋์ด์ง๋ ์๋ ํ์ ๋ง์์ค๋ค.
    * ๊ธฐ์กด์ nested ๋ฐฉ์์ผ๋ก SASS๋ฅผ ์์ฑํ๋ฉด, ์ปดํ์ด ์ ์๋ ํ์ด ๋๋ ์์ด ๊ธธ์ด์ง๋ ๊ฒฝ์ฐ๊ฐ ์์ผ๋ BEM ๋ฐฉ์์ ์ฐ๋ฉด ๋๋๋๋ ์๋ฆฌ๋จผํธ๋ผ์ ๊ตณ์ด ๊น๊ฒ nestedํ  ํ์๊ฐ ์์ด์ง๋ค.

### ๋จ์ 

1. ํด๋์ค ๋ค์์ด ๋๋ฌด ๊ธธ๋ค.
2. ๋๋ธํด๋ฆญ ์ ํ์ด ๋ถํธํ๋ค.