# Javascript란?

![js](https://images.velog.io/images/kakasoo/post/ada6c1eb-0796-4881-8658-567d6e09ee15/1_6ahbWjp_g9hqhaTDSJOL1Q.png)

* 자바스크립트는 <b>웹 페이지 상호작용</b>을 손쉽게 추가하기 위해 만든 언어
* DHTML(Dynamic HTML) AJAX(Asynchoronous Javascript And XML, 비동기식 자바스크립트)를 거치며 더 활발히 사용
* 노드가 등장함에 따라 풀스택 어플리케이션을 개발하는데 쓰이는 언어가 되었다.
<br><br>

# 구문(Syntax)과 기본문법

* <b>변수(Variable)</b>는 값(Value)을 저장(할당)하고 그 저장된 값을 참조하기 위해 사용한다.
* 한번 쓰고 버리는 값이 아닌 <b>유지(캐싱)</b>할 필요가 있는 값은 변수에 담아 사용한다.
* 변수에 상징적인 이름을 붙여 값의 의미를 명확히 할 수 있어 코드의 가독성이 좋아진다.
* 변수는 위치(주소)를 기억하는 저장소이다.
* 위치란 메모리 상의 주소(address)를 의미
* 즉, 변수란 메모리주소(Memory Address)에 접근하기 위해 사람이 이해라 수 있는 언어로 지정한 <b>식별자(Identifier)</b>이다.
* 식별자는 특정 규칙을 따른다.

### 식별자 규칙

1. 문자, 밑줄(_) 혹은 달러기호($)로 시작한다.
2. 숫자는 식별자의 시작부분 외에 위치할 수 있다.
3. 대소문자를 구분하며, 문자는 "A"부터 "z"까지 모두 포함한다.
4. 예약어(for, if, int 등)는 사용 불가  
ex) 적절한 이름 : Number_hits, temp99, $credit, _name 등
<br><br>

## ES6에서 변수 선언  

### const  

* 상수(const)는 변경할 수 없는 변수
* 상수가 없던 시절에는 모든 값을 변수에 넣어 사용
* 하지만 변수는 값을 변경할 수 있다.
```javascript
//상수 사용 이전
var study = true;
study = false;
console.log(study) // false

//상수 사용 
const study = true;
study = false;
// Uncaught TypeError가 발생
// const로 선언 후 값을 변경하려고 시도하면 오류 발생
```

### let  

* 기존 var은 if/else와 같은 블록 안에서 변수를 새로 만들면 그 변수의 영역이 전역변수로 설정되었다.
```javascript
var study = "자바스크립트";

if(study){
    var study = "리액트";
    console.log('공부하자', study); // 공부하자 리액트
}

console.log('재밌다', study); // 재밌다 리액트
```
* let을 사용하면 <b>변수 영역을 코드 블록 안으로 한정</b>시킬 수 있다.
* 즉, 전역 변수의 값을 보호할 수 있다.
```javascript
var study = "자바스트립트";

if(study){
	let study = "리액트";
	console.log('공부하자', study); // 공부하자 리액트
}

console.log('재밌다', study); // 재밌다 자바스크립트
```
<br><br>

## 템플릿 문자열  

* 템플릿 문자열은 문자열 연결 대신 사용할 수 있다. 그러면 중간에 변수를 삽입할 수도 있다.
* 전통적인 문자열 연결은 '+'기호로 문자열과 변수를 이음
* 템플릿에서는 `${}` 를 사용해 문자열 안에 변수를 집어넣을 수 있기 때문에 문자열을 단 하나만 사용해도 된다.
```javascript
console.log(`${lastname}, ${firstname} ${middlename}`);//백틱(`) 필수!
```
* 템플릿 문자열은 공백(빈 칸뿐 아니라 탭, 개행문자 등도 포함)을 유지한다.
* 전자우편 템플릿이나 코드예제 등 공백이 들어가야 하는 문자열을 사용할 때 사용한다.
```javascript
`
${firstname} 님께,

${event} 티켓 ${qty}건을 구매해주셔서 감사합니다.

주문 상세 정보 :
	${lastname} ${firstname} ${middlename}
    ${qty} x $${price} = $${qty*price}	공연 : ${event}
    
공연 30분 전까지 배부처에서 티켓을 수령하시기 바랍니다.
감사합니다 :)

${ticketAgent} 드림
`
```

## 디폴트 파라미터

* C++나 Python 같은 언어에서는 함수의 인자로 디폴트 값을 선언할 수 있다.
* ES6 명세에도 디폴트 파라미터가 추가되었다.
* 따라서 함수를 호출하면서 값을 지정하지 않으면 디폴트 값을 사용된다.
```javascript
function logActivity(name="EZ", activity="서핑"){
    console.log(`${name}은(는) ${activity}을(를) 좋아합니다.`);
}
```
* logActivity 함수를 호출하면서 인자를 지정하지 않아도 디폴트 값을 사용해서 함수가 정상적으로 실행
* 문자열뿐 아니라 어떤 타입의 값도 사용할 수 있다.
```javascript
var dafaultPerson = {
	name: {
    	first : "Z",
        last : "E",    
    },
    favActivity: "서핑"
}

function logActivity(p = dafaultPerson){
	console.log(`${p.name.first}은(는) ${favActivity}을(를) 좋아합니다.`);
}
```
<br><br>

## 화살표 함수

* 화살표 함수(arrow function)는 ES6에 새로 추가된 유용한 기능
* <b>function 키워드 없이</b>도 함수를 만들 수 있으며, <b>return을 사용하지 않아도 식을 계산한 값이 자동으로 반환</b>된다.
```javascript
//기존 함수 방식
var lodify = function(name) {
    return `열심히 공부하는 ${name}`;
}
console.log(lodify("EZ"));//열심히 공부하는 EZ

//화살표 함수 방식
var lodify = name => `열심히 공부하는 ${name}`;
```
* 화살표를 사용하면 모든 함수 정의를 한 줄로 끝낼 수 있다.
* function 키워드를 없앴고 어떤 값을 반환하는지 화살표가 지정하기 때문에 return도 없앴다.
* 또 다른 장점은 함수가 파라미터를 단 하나만 받는 경우 파라미터 주변의 괄호를 생략해도 된다는 것이다.
* 파라미터가 2개 이상이라면 괄호가 필요
```javascript
var lodify = (name, study) => `${study}를 공부하는 ${name}`;
console.log(lodify("EZ", "react")); //react를 공부하는 EZ
```

<br><br>

## 데이터타입  

1. 기본 타입(원시 타입 : Primitvie Type)  
   * 숫자(number)
   * 문자열(string)
   * 논리값(boolean)
   * undeined
   * null
   * 심벌(symbol)

2. 참조 타입(객체 타입 : Object/Reference Type)
   * 객체
   * 배열
   * 함수
   * 정규 표현식
