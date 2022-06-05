# 💻 개념 이해하기

## 호이스팅

> 호이스팅(Hoisting) : 변수나 함수의 호출 코드가 선언 코드보다 아래쪽에 있음에도 에러가 발생하지 않고, 마치 선언 코드가 호출코드보다 더 위에 선언된 것과 같이 동작하는 특성
* 호이스팅이 발생하는 이유
    1. 자바스크립트 엔진은 함수선언문 해석 -> 변수 초기화 -> 코드실행 순서로 진행
    2. 코드를 실행할 땐 이미 함수 선언문과 변수가 생성되어 있는 상태이기 때문에
    3. 어디에서든 함수나 변수를 호출할 수 있다.(제일 윗 줄에서도 호출 가능)

### 호이스팅 예시

1. 매개 변수 & 변수의 호이스팅

```javascript
    function hello(x) { //수집대상 1(매개변수)
        console.log(x);
        var x; //수집대상 2(선언된 변수)
        console.log(x);
        var x = 2; //수집대상 3(선언된 변수)
        console.log(x);
    }

    hello(1);
```
↓
```javascript
    function hello( ) { 
        var x; //수집대상 1(매개변수)
        var x; //수집대상 2(선언된 변수)
        var x  //수집대상 3(선언된 변수)
        x = 1; //함수 호출시 매개변수에 할당된 값
        console.log(x);
        console.log(x);
        x = 2;
        console.log(x);
    }

    hello(1);
```

2. 함수 선언 호이스팅

```javascript
   function a () {
        console.log(b); // (1)
        var b = 'bbb'; //수집대상 1(선언된 **변수**)
        console.log(b); //(2)
        function b () {} //수집대상 2(선언된 **함수**)
        console.log(b); //(3)
    };
    a();
```
↓
```javascript
    function a () {
        var b; //수집대상 1(선언된 **변수**) ====> 변수는 선언부만 끌어올려짐(hoisted)
        function b () {} //수집대상 2(선언된 **함수**)	===> 함수는 전체가 끌려올라감
        console.log(b); // (1)
        b = 'bbb';
        console.log(b); //(2)
        console.log(b); //(3)
    };
    a();
```

## 이벤트 버블링

> 특정 화면 요소에서 이벤트가 발생했을 때 해당 이벤트가 더 상위의 화면 요소들로 전달되어 가는 특성을 의미

## 스코프

Scope를 번역하면 **범위**라는 뜻을 가지고 있다.
> 즉, 스코프란 '변수에 접근할 수 있는 범위'라고 할 수 있다.

* 자바스크립트에서 스코프는 global(전역)과 local(지역)으로 나뉜다.
* 전역 스코프는 전역에 선언되어있어 어느 곳에서든 해당 변수에 접근할 수 있다.
* 지역 스코프는 해당 지역에서만 접근할 수 있어 지역을 벗어난 곳에서는 접근 할 수 없다.
* 자바스크립트에서 함수를 선언하면 함수를 선언할 때마다 새로운 스코프를 생성하게 된다.
* 그러므로 함수 몸체에 선언한 볒ㄴ수는 해당 함수 몸체 안에서만 접근할 수 있다. => <b>함수 스코프</b>

```javascript
var a = 1; // 전역 스코프
function print() { // 지역(함수) 스코프
 var a = 111;
 console.log(a);
}
print(); // 111
console.log(a); // 1
```

## 프로토타입

[프로토타입](https://velog.io/@adam2/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-Prototype-%EC%99%84%EB%B2%BD-%EC%A0%95%EB%A6%AC)

## Shadow DOM

> Shadow DOM은 DOM의 구조를 가지고 있으나 외부에는 노출되지 않은 DOM을 말하며 DOM의 구조를 캡슐화할 때 사용한다.

* 일반적인 외부의 style은 적용되지 않고 Shadow DOM을 추가하거나 접근하기 위해서는 별도의 방법이 필요
* 템플릿 엘리먼트를 이용해 만들어진 데코레이터나 커스텀 엘리먼트는 모두 Shadow DOM으로 만들어진다. 다만, 데코레이터에서 만들어진 Shadow DOM은 스크립트로 접근 및 수정 불가
* 그에 비해 커스텀 엘리먼트로 만들어진 Shadow DOM은 스크립트로 수정할 수 있다.  

왼쪽이 일반적인 DOM 트리, 오른쪽이 Shadow DOM 트리
![ShadowDOM](https://s1.md5.ltd/image/9f0e28422e6af5d1c2331df55268d95c.png)

### 일반DOM 트리

```
<x-slide is="x-slide">  
    <li><img src="http://helloworld.naver.com/img/1.jpeg" alt="1.jpeg" width="500px" height="333px" style=""></li>
    <li><img src="http://helloworld.naver.com/img/2.jpeg" alt="2.jpeg" width="500px" height="333px" style=""></li>
    <li><img src="http://helloworld.naver.com/img/3.jpeg" alt="3.jpeg" width="500px" height="333px" style=""></li>
    <li><img src="http://helloworld.naver.com/img/4.jpeg" alt="4.jpeg" width="500px" height="333px" style=""></li>
</x-slide>  
```

### Shadow DOM 트리

```
<element name="x-slide" extends="ul" constructor="SlideControl">  
    <template>

        <div class="slide">
            <ul>
                <content select="li"></content>
            </ul>
        </div>
    </template>
</element>  
```

* 기존의 컴포넌트는 일반적인 DOM 트리가 렌더링된 후 해당 DOM 트리를 변경하기 때문에 리플로(reflow)와 리페인트(repaint)등의 큰 비용이 발생
* Shadow DOM을 사용하면 Shadow host, 위의 코드의 x-slide 엘리먼트를 만나는 순간 Shadow DOM이 렌더링 된다.

## Strict

* strict 모드는 ES5에 추가된 키워드다.
* strict 모드는 자바스크립트가 묵인했던 에러들의 에러 메시지를 발생시킨다.
* 엄격하게 문법 검사를 하겠다는 뜻

### Strict 모드 선언

> 스크립트의 시작 혹은 함수의 시작 부분에 <b>"use strict"</b>를 선언하면 strict모드로 코드를 작성할 수 있다.