# 💻 모듈러 JavaScript와 ES6+  

## 모듈(Module)이란?

모듈이란 여러 기능들에 관한 코드가 오며이쓴 하나의 파일로 다음과 같은 것들을 위해 사용한다.

* <b>유지보수성</b> : 기능들이 모듈화가 잘 되어있다면, 의존성을 그만큼 줄일 수 있기 때문에 어떤 기능을 개성한다던가 수정할 때 훨씬 편하게 할 수 있다.
  
* 네임스페이스화 : 자바스크립트에서 전역변수는 전역공간을 가지기 때문에 코드의 양이 많아질수록 겹치는 네임스페이가 많아질 수 있다. 그러나 모듈로 분리하면 모듈만의 네임스페이스를 갖기 때문에 그 문제가 해결된다. 
> 네임스페이스 : 개체를 구분할 수 있는 범위를 나타내는 말로 일반적으로 하나의 이름 공간에서는 하나의 이름이 단 하나의 개체만을 가리키게 된다.

* 재사용성 : 똑같은 코드를 반복하지 않고 모듈로 분리시켜  필요할 때마다 사용할 수 있다.

이런 장점들을 살리기 위해 모듈 개념이 필요했고 자바스크립트에선 모듈을 개발하기 위한 여러가지 시도들이 있었다. 


## CommonJS

* 자바스크립트의 공식 스펙이 브라우저만 지원햇기 때문이 이를 서버사이드 및 데스크탑 어플리케이션에서 지원하기 위한 노력이 있었다. 그걸 위해 만든 그룹이 CommonJS이며 자바스크립트가 범용적인 언어로 쓰이기 위한 스펙을 정의한다.
* 범용적인 언어로 만들기 위해 모듈화의 개념이 필요했고 이 그룹만의 모듈 방식을 정의한 것이 <b>CommonJS 방식 모듈화</b>다.
* 다른 모듈을 사용할 때는 `require`를, 모듈을 해당 스코프 밖으로 보낼 때에는 `mocule.exports`를 사용한다.  
<br>

> hello owrld를 출력하는 함수를 가진 파일을 a.js, 함수를 가져와서 사용하는 파일을 b.js라고 하면 다음과 같이 사용할 수 있다.

### a.js

```javascript
const printHelloWorld = () => {
  console.log('Hello Wolrd');
};

module.exports = {
  printHelloWorld
};
```

### b.js

```javascript
const func = require('./a.js'); // 같은 디렉토리에 있다고 가정
func.printHelloWorld();
```

여기서 module.exports의 module은 현재 모듈에 대한 정보를 갖고 있는 객체이다. 이는 예약어미며 그 안에 id, path, parent 등의 속성이 있고 exports 객체를 가지고 있다.  
<br>

## ES6 Module

ES6 모듈 시스템은 CommonJS 모듈 시스템보다 최신 스펙이며 여러 이점이 있다.  
* import, from, export, default 처럼 <b>모듈 관리 전용 키워드</b>를 사용
* 비동기 방식으로 작동하고 모듈에서 실제로 쓰이는 부분만 불러오기 때문에 성능과 메모리 부분에서도 유리하다.

### Multipel Objects export/import

### export

* CommonJS에서는 내보낼 복수 객체들을 exports 변수의 속성으로 할당하는 방식을 사용했으나, ES6에서는 import 키워드의 짝꿍인 <b>export</b> 키워드를 사용해 명시적으로 선언한다.
* 내보내는 변수나 함수의 이름이 그대로 불러낼 때 사용하게 되는 이름이 되기 때문에 이를 <b>Named Exports</b>라고 한다.

> 아래는 미국과 캐나다 달러는 상호 변환해주는 자바스크립트 예제 코드이다. 이 파일에는 3개의 함수가 있으며 2개의 함수만 다른 파일에서 접근할 수 있도록 내보내기를 했다. 첫 번째 방법은 선언과 동시에 내보내고 두 번째 방법은 선언 후에 별도로 내보내는 것이다.

### currendy-functions.js

```javascript
const exchangeRate = 0.91;

// 내보내지 않음
function roundTwoDecimals(amount) {
    return Math.round(amount * 100) / 100;
}

// 첫번째 내보내기 방법
export function canadianToUs(canadian) {
    return roundTwoDecimals(canadian * exchangeRate);
}

// 두번째 내보내기 방법
const usToCanadian = function(us) {
    return roundTwoDecimals(us / exchangeRate)
}
export { usToCanadian }
```
<br>

### Import

* 여러 객체(Named Exports)를 불러올 때는 ES6의 `Destructuring(구조분해할당)` 문법을 사용해 필요한 객체만 선택적으로 전역에서 사용하거나, 모든 객체에 별명을 붙이고 그 별명을 통해 접근할 수도 있다.

### test-curency-function.js

```javascript
// Desturturing
import { canadianToUs } from "./currency-functions"

console.log("50 Canadian dollars equals this amount of US dollars:");
console.log(canadianToUs(50));

// Alias
import * as currency from "./currency-functions"

console.log("30 US dollars equals this amount of Canadian dollars:");
console.log(currency.usToCanadian(30));
```

### 실행결과

```
50 Canadian dollars equals this amount of US dollars:
45.5
30 US dollars equals this amount of Canadian dollars:
32.97
```

<br>

### Single Object export/import

### Export

* CommonJs에서 내보낼 단일 객체를 module.exprots변수에 할당하는 방식을 사용했으나 ES6에서는 `export default` 키워드를 사용해 명시적으로 선언
* 하나의 모듈에서 하나의 객체만 내보내기 때문에 이를 `Default Export`라고 함

> 아래 예제는 두개 함수를 객체로 묶어서 내보내기를 한 코드이다. 이름이 필요없기 때문에 별도 변수 할당이 없이 바로 객체를 내보내기 할 수 있다. 내보낼 때 어떤 이름도 지정하지 않기 때문에 불러올 때도 아무 이름이나 사용할 수 있다.

### currency-object.js

```javascript
const exchangeRate = 0.91;

// 내보내지 않음
function roundTWoDecimals(amount) {
    return Math.round(amount * 100) / 100;
}

// 내보내기
export default {
    canadianToUs(canadian){
        return roundTwoDecimals(canadian * exchangeRate);
    },
    usToCanadian: function(us){
        return roundTwoDecimals(us / exhangeRate);
    },
}
```

<br>

변수에 할당하여 내보내기 하고 싶다면 다음과 같이 작성할 수 있다.

```javascript
const obj = {
  canadianToUs(canadian) {
    return roundTwoDecimals(canadian * exchangeRate)
  },
}

obj.usToCanadian = function (us) {
  return roundTwoDecimals(us / exchangeRate)
}

export default obj
```

<br>

### Import

* 하나의 객체(Default Export)를 불러올 때는 간단하게 `import` 키워드를 사용해 아무 이름이나 원하는 이름을 주고 해당 객체를 통해 속성에 접근하면 된다.

### test-currendy-object.js

```javascript
import currency from "./currency-object"

console.log("50 Canadian dollars equals this amount of US dollars:")
console.log(currency.canadianToUs(50))

console.log("30 US dollars equals this amount of Canadian dollars:")
console.log(currency.usToCanadian(30))
```

### 실행결과

```
50 Canadian dollars equals this amount of US dollars:
45.5
30 US dollars equals this amount of Canadian dollars:
32.97
```

<br>

> 주의점 : Babel없이 순수하게 Node.js 최신 버전으로 ES 모듈을 사용 시 import 할 때 .js 확장자를 붙여야 한다.

### require()가 있는데 improt가 생긴 이유

* `require`와 `import`에 대해 비교하기 위해서는 우선 CommonJS와 AMD(Asynchronous Module Dfinition), ES6 내장모듈과 같은 자바스크립트의 모듈 시스템에 대해 알고 있어야 한다.

* 기존의 자바스크립트는 모듈이라는 개념이 부족하여 각 모듈 간의 의존성 처리에 제한이 있었다.
* 고전적인 웹 프로젝트에서 자바스크립트를 상요하는 방법은 HTML 파일 내부에 `<script>`태그를 삽입하여 모듈을 로드했다.
* <b>하지만 이 방식은 자바스크립트 파일끼리 서로 모듈을 공유하는데 제약이 없다는 문제가 있다.</b>
* `<script>` 태그롸 로드된 모듈은 모두 window 객체의 속성이기 때문에 서로 다른 파일에 위치하면서도 모든 객체를 공유할 수 있기 때문
<br><br>

* 각 자바스크립트 파일이 독립적으로 존재하지 못해 발생하는 여러 문제들( 다른 파일에서 같은 이름의 변수를 사용하는 경우 등) 때눔에 하나의 모듈로 관리하기 위한 다양한 패턴(Module Pattern, 즉시 실행 함수 등)을 사용하여 의존성을 관리할 수 밖에 없었다.
* 이를 해결하기 위한 수단으로 모듈이라는 개념을 도입하여 정의한 방법이 CommonJS와 AMD이다.
* 내부적으로 모듈 서로 간의 의존성이 지원되지 않는 상태로 만들어졌으며, ES6에 이르러 언어 내부적으로 자바스크립트 모듈 의존성을 지원하게 되었다.(export, import)

<br>

### 모듈 정의 방식의 혼용

* ES6 모듈은 기본적으로 CommonJs와 AMD 모듈을 혼용해서 사용할 수 있다.
* 모듈을 가져오는 부분에 `require()`와 `import`를 같이 사용하더라도 문제없이 동작한다.
* `import`는 ES6 문법이라 현재 사용되는 브라우저에서는 지원하지 않지만, babel과 같은 트랜스파일러가 해결해줄 수 있다.  