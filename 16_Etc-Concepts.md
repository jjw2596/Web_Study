# π» κ°λ μ΄ν΄νκΈ°

## π νΈμ΄μ€ν

> νΈμ΄μ€ν(Hoisting) : λ³μλ ν¨μμ νΈμΆ μ½λκ° μ μΈ μ½λλ³΄λ€ μλμͺ½μ μμμλ μλ¬κ° λ°μνμ§ μκ³ , λ§μΉ μ μΈ μ½λκ° νΈμΆμ½λλ³΄λ€ λ μμ μ μΈλ κ²κ³Ό κ°μ΄ λμνλ νΉμ±
* νΈμ΄μ€νμ΄ λ°μνλ μ΄μ 
    1. μλ°μ€ν¬λ¦½νΈ μμ§μ ν¨μμ μΈλ¬Έ ν΄μ -> λ³μ μ΄κΈ°ν -> μ½λμ€ν μμλ‘ μ§ν
    2. μ½λλ₯Ό μ€νν  λ μ΄λ―Έ ν¨μ μ μΈλ¬Έκ³Ό λ³μκ° μμ±λμ΄ μλ μνμ΄κΈ° λλ¬Έμ
    3. μ΄λμμλ  ν¨μλ λ³μλ₯Ό νΈμΆν  μ μλ€.(μ μΌ μ μ€μμλ νΈμΆ κ°λ₯)

### νΈμ΄μ€ν μμ

1. λ§€κ° λ³μ & λ³μμ νΈμ΄μ€ν

```javascript
    function hello(x) { //μμ§λμ 1(λ§€κ°λ³μ)
        console.log(x);
        var x; //μμ§λμ 2(μ μΈλ λ³μ)
        console.log(x);
        var x = 2; //μμ§λμ 3(μ μΈλ λ³μ)
        console.log(x);
    }

    hello(1);
```
β
```javascript
    function hello( ) { 
        var x; //μμ§λμ 1(λ§€κ°λ³μ)
        var x; //μμ§λμ 2(μ μΈλ λ³μ)
        var x  //μμ§λμ 3(μ μΈλ λ³μ)
        x = 1; //ν¨μ νΈμΆμ λ§€κ°λ³μμ ν λΉλ κ°
        console.log(x);
        console.log(x);
        x = 2;
        console.log(x);
    }

    hello(1);
```

2. ν¨μ μ μΈ νΈμ΄μ€ν

```javascript
   function a () {
        console.log(b); // (1)
        var b = 'bbb'; //μμ§λμ 1(μ μΈλ **λ³μ**)
        console.log(b); //(2)
        function b () {} //μμ§λμ 2(μ μΈλ **ν¨μ**)
        console.log(b); //(3)
    };
    a();
```
β
```javascript
    function a () {
        var b; //μμ§λμ 1(μ μΈλ **λ³μ**) ====> λ³μλ μ μΈλΆλ§ λμ΄μ¬λ €μ§(hoisted)
        function b () {} //μμ§λμ 2(μ μΈλ **ν¨μ**)	===> ν¨μλ μ μ²΄κ° λλ €μ¬λΌκ°
        console.log(b); // (1)
        b = 'bbb';
        console.log(b); //(2)
        console.log(b); //(3)
    };
    a();
```

## π μ΄λ²€νΈ λ²λΈλ§

> νΉμ  νλ©΄ μμμμ μ΄λ²€νΈκ° λ°μνμ λ ν΄λΉ μ΄λ²€νΈκ° λ μμμ νλ©΄ μμλ€λ‘ μ λ¬λμ΄ κ°λ νΉμ±μ μλ―Έ

## π μ€μ½ν

Scopeλ₯Ό λ²μ­νλ©΄ **λ²μ**λΌλ λ»μ κ°μ§κ³  μλ€.
> μ¦, μ€μ½νλ 'λ³μμ μ κ·Όν  μ μλ λ²μ'λΌκ³  ν  μ μλ€.

* μλ°μ€ν¬λ¦½νΈμμ μ€μ½νλ global(μ μ­)κ³Ό local(μ§μ­)μΌλ‘ λλλ€.
* μ μ­ μ€μ½νλ μ μ­μ μ μΈλμ΄μμ΄ μ΄λ κ³³μμλ  ν΄λΉ λ³μμ μ κ·Όν  μ μλ€.
* μ§μ­ μ€μ½νλ ν΄λΉ μ§μ­μμλ§ μ κ·Όν  μ μμ΄ μ§μ­μ λ²μ΄λ κ³³μμλ μ κ·Ό ν  μ μλ€.
* μλ°μ€ν¬λ¦½νΈμμ ν¨μλ₯Ό μ μΈνλ©΄ ν¨μλ₯Ό μ μΈν  λλ§λ€ μλ‘μ΄ μ€μ½νλ₯Ό μμ±νκ² λλ€.
* κ·Έλ¬λ―λ‘ ν¨μ λͺΈμ²΄μ μ μΈν λ³γ΄μλ ν΄λΉ ν¨μ λͺΈμ²΄ μμμλ§ μ κ·Όν  μ μλ€. => <b>ν¨μ μ€μ½ν</b>

```javascript
var a = 1; // μ μ­ μ€μ½ν
function print() { // μ§μ­(ν¨μ) μ€μ½ν
 var a = 111;
 console.log(a);
}
print(); // 111
console.log(a); // 1
```

## π νλ‘ν νμ

[νλ‘ν νμ](https://velog.io/@adam2/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-Prototype-%EC%99%84%EB%B2%BD-%EC%A0%95%EB%A6%AC)

## π Shadow DOM

> Shadow DOMμ DOMμ κ΅¬μ‘°λ₯Ό κ°μ§κ³  μμΌλ μΈλΆμλ λΈμΆλμ§ μμ DOMμ λ§νλ©° DOMμ κ΅¬μ‘°λ₯Ό μΊ‘μνν  λ μ¬μ©νλ€.

* μΌλ°μ μΈ μΈλΆμ styleμ μ μ©λμ§ μκ³  Shadow DOMμ μΆκ°νκ±°λ μ κ·ΌνκΈ° μν΄μλ λ³λμ λ°©λ²μ΄ νμ
* ννλ¦Ώ μλ¦¬λ¨ΌνΈλ₯Ό μ΄μ©ν΄ λ§λ€μ΄μ§ λ°μ½λ μ΄ν°λ μ»€μ€ν μλ¦¬λ¨ΌνΈλ λͺ¨λ Shadow DOMμΌλ‘ λ§λ€μ΄μ§λ€. λ€λ§, λ°μ½λ μ΄ν°μμ λ§λ€μ΄μ§ Shadow DOMμ μ€ν¬λ¦½νΈλ‘ μ κ·Ό λ° μμ  λΆκ°
* κ·Έμ λΉν΄ μ»€μ€ν μλ¦¬λ¨ΌνΈλ‘ λ§λ€μ΄μ§ Shadow DOMμ μ€ν¬λ¦½νΈλ‘ μμ ν  μ μλ€.  

μΌμͺ½μ΄ μΌλ°μ μΈ DOM νΈλ¦¬, μ€λ₯Έμͺ½μ΄ Shadow DOM νΈλ¦¬
![ShadowDOM](https://s1.md5.ltd/image/9f0e28422e6af5d1c2331df55268d95c.png)

### μΌλ°DOM νΈλ¦¬

```
<x-slide is="x-slide">  
    <li><img src="http://helloworld.naver.com/img/1.jpeg" alt="1.jpeg" width="500px" height="333px" style=""></li>
    <li><img src="http://helloworld.naver.com/img/2.jpeg" alt="2.jpeg" width="500px" height="333px" style=""></li>
    <li><img src="http://helloworld.naver.com/img/3.jpeg" alt="3.jpeg" width="500px" height="333px" style=""></li>
    <li><img src="http://helloworld.naver.com/img/4.jpeg" alt="4.jpeg" width="500px" height="333px" style=""></li>
</x-slide>  
```

### Shadow DOM νΈλ¦¬

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

* κΈ°μ‘΄μ μ»΄ν¬λνΈλ μΌλ°μ μΈ DOM νΈλ¦¬κ° λ λλ§λ ν ν΄λΉ DOM νΈλ¦¬λ₯Ό λ³κ²½νκΈ° λλ¬Έμ λ¦¬νλ‘(reflow)μ λ¦¬νμΈνΈ(repaint)λ±μ ν° λΉμ©μ΄ λ°μ
* Shadow DOMμ μ¬μ©νλ©΄ Shadow host, μμ μ½λμ x-slide μλ¦¬λ¨ΌνΈλ₯Ό λ§λλ μκ° Shadow DOMμ΄ λ λλ§ λλ€.

## π Strict

* strict λͺ¨λλ ES5μ μΆκ°λ ν€μλλ€.
* strict λͺ¨λλ μλ°μ€ν¬λ¦½νΈκ° λ¬΅μΈνλ μλ¬λ€μ μλ¬ λ©μμ§λ₯Ό λ°μμν¨λ€.
* μκ²©νκ² λ¬Έλ² κ²μ¬λ₯Ό νκ² λ€λ λ»

### Strict λͺ¨λ μ μΈ

> μ€ν¬λ¦½νΈμ μμ νΉμ ν¨μμ μμ λΆλΆμ <b>"use strict"</b>λ₯Ό μ μΈνλ©΄ strictλͺ¨λλ‘ μ½λλ₯Ό μμ±ν  μ μλ€.