# π» λͺ¨λλ¬ JavaScriptμ ES6+  

## π λͺ¨λ(Module)μ΄λ?

λͺ¨λμ΄λ μ¬λ¬ κΈ°λ₯λ€μ κ΄ν μ½λκ° μ€λ©°μ΄μ΄ νλμ νμΌλ‘ λ€μκ³Ό κ°μ κ²λ€μ μν΄ μ¬μ©νλ€.

* <b>μ μ§λ³΄μμ±</b> : κΈ°λ₯λ€μ΄ λͺ¨λνκ° μ λμ΄μλ€λ©΄, μμ‘΄μ±μ κ·Έλ§νΌ μ€μΌ μ μκΈ° λλ¬Έμ μ΄λ€ κΈ°λ₯μ κ°μ±νλ€λκ° μμ ν  λ ν¨μ¬ νΈνκ² ν  μ μλ€.
  
* λ€μμ€νμ΄μ€ν : μλ°μ€ν¬λ¦½νΈμμ μ μ­λ³μλ μ μ­κ³΅κ°μ κ°μ§κΈ° λλ¬Έμ μ½λμ μμ΄ λ§μμ§μλ‘ κ²ΉμΉλ λ€μμ€νμ΄κ° λ§μμ§ μ μλ€. κ·Έλ¬λ λͺ¨λλ‘ λΆλ¦¬νλ©΄ λͺ¨λλ§μ λ€μμ€νμ΄μ€λ₯Ό κ°κΈ° λλ¬Έμ κ·Έ λ¬Έμ κ° ν΄κ²°λλ€. 
> λ€μμ€νμ΄μ€ : κ°μ²΄λ₯Ό κ΅¬λΆν  μ μλ λ²μλ₯Ό λνλ΄λ λ§λ‘ μΌλ°μ μΌλ‘ νλμ μ΄λ¦ κ³΅κ°μμλ νλμ μ΄λ¦μ΄ λ¨ νλμ κ°μ²΄λ§μ κ°λ¦¬ν€κ² λλ€.

* μ¬μ¬μ©μ± : λκ°μ μ½λλ₯Ό λ°λ³΅νμ§ μκ³  λͺ¨λλ‘ λΆλ¦¬μμΌ  νμν  λλ§λ€ μ¬μ©ν  μ μλ€.

μ΄λ° μ₯μ λ€μ μ΄λ¦¬κΈ° μν΄ λͺ¨λ κ°λμ΄ νμνκ³  μλ°μ€ν¬λ¦½νΈμμ  λͺ¨λμ κ°λ°νκΈ° μν μ¬λ¬κ°μ§ μλλ€μ΄ μμλ€. 


## π CommonJS

* μλ°μ€ν¬λ¦½νΈμ κ³΅μ μ€νμ΄ λΈλΌμ°μ λ§ μ§μνκΈ° λλ¬Έμ΄ μ΄λ₯Ό μλ²μ¬μ΄λ λ° λ°μ€ν¬ν μ΄νλ¦¬μΌμ΄μμμ μ§μνκΈ° μν λΈλ ₯μ΄ μμλ€. κ·Έκ±Έ μν΄ λ§λ  κ·Έλ£Ήμ΄ CommonJSμ΄λ©° μλ°μ€ν¬λ¦½νΈκ° λ²μ©μ μΈ μΈμ΄λ‘ μ°μ΄κΈ° μν μ€νμ μ μνλ€.
* λ²μ©μ μΈ μΈμ΄λ‘ λ§λ€κΈ° μν΄ λͺ¨λνμ κ°λμ΄ νμνκ³  μ΄ κ·Έλ£Ήλ§μ λͺ¨λ λ°©μμ μ μν κ²μ΄ <b>CommonJS λ°©μ λͺ¨λν</b>λ€.
* λ€λ₯Έ λͺ¨λμ μ¬μ©ν  λλ `require`λ₯Ό, λͺ¨λμ ν΄λΉ μ€μ½ν λ°μΌλ‘ λ³΄λΌ λμλ `mocule.exports`λ₯Ό μ¬μ©νλ€.  
<br>

> hello owrldλ₯Ό μΆλ ₯νλ ν¨μλ₯Ό κ°μ§ νμΌμ a.js, ν¨μλ₯Ό κ°μ Έμμ μ¬μ©νλ νμΌμ b.jsλΌκ³  νλ©΄ λ€μκ³Ό κ°μ΄ μ¬μ©ν  μ μλ€.

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
const func = require('./a.js'); // κ°μ λλ ν λ¦¬μ μλ€κ³  κ°μ 
func.printHelloWorld();
```

μ¬κΈ°μ module.exportsμ moduleμ νμ¬ λͺ¨λμ λν μ λ³΄λ₯Ό κ°κ³  μλ κ°μ²΄μ΄λ€. μ΄λ μμ½μ΄λ―Έλ©° κ·Έ μμ id, path, parent λ±μ μμ±μ΄ μκ³  exports κ°μ²΄λ₯Ό κ°μ§κ³  μλ€.  
<br>

## π ES6 Module

ES6 λͺ¨λ μμ€νμ CommonJS λͺ¨λ μμ€νλ³΄λ€ μ΅μ  μ€νμ΄λ©° μ¬λ¬ μ΄μ μ΄ μλ€.  
* import, from, export, default μ²λΌ <b>λͺ¨λ κ΄λ¦¬ μ μ© ν€μλ</b>λ₯Ό μ¬μ©
* λΉλκΈ° λ°©μμΌλ‘ μλνκ³  λͺ¨λμμ μ€μ λ‘ μ°μ΄λ λΆλΆλ§ λΆλ¬μ€κΈ° λλ¬Έμ μ±λ₯κ³Ό λ©λͺ¨λ¦¬ λΆλΆμμλ μ λ¦¬νλ€.

### Multipel Objects export/import

### export

* CommonJSμμλ λ΄λ³΄λΌ λ³΅μ κ°μ²΄λ€μ exports λ³μμ μμ±μΌλ‘ ν λΉνλ λ°©μμ μ¬μ©νμΌλ, ES6μμλ import ν€μλμ μ§κΏμΈ <b>export</b> ν€μλλ₯Ό μ¬μ©ν΄ λͺμμ μΌλ‘ μ μΈνλ€.
* λ΄λ³΄λ΄λ λ³μλ ν¨μμ μ΄λ¦μ΄ κ·Έλλ‘ λΆλ¬λΌ λ μ¬μ©νκ² λλ μ΄λ¦μ΄ λκΈ° λλ¬Έμ μ΄λ₯Ό <b>Named Exports</b>λΌκ³  νλ€.

> μλλ λ―Έκ΅­κ³Ό μΊλλ€ λ¬λ¬λ μνΈ λ³νν΄μ£Όλ μλ°μ€ν¬λ¦½νΈ μμ  μ½λμ΄λ€. μ΄ νμΌμλ 3κ°μ ν¨μκ° μμΌλ©° 2κ°μ ν¨μλ§ λ€λ₯Έ νμΌμμ μ κ·Όν  μ μλλ‘ λ΄λ³΄λ΄κΈ°λ₯Ό νλ€. μ²« λ²μ§Έ λ°©λ²μ μ μΈκ³Ό λμμ λ΄λ³΄λ΄κ³  λ λ²μ§Έ λ°©λ²μ μ μΈ νμ λ³λλ‘ λ΄λ³΄λ΄λ κ²μ΄λ€.

### currendy-functions.js

```javascript
const exchangeRate = 0.91;

// λ΄λ³΄λ΄μ§ μμ
function roundTwoDecimals(amount) {
    return Math.round(amount * 100) / 100;
}

// μ²«λ²μ§Έ λ΄λ³΄λ΄κΈ° λ°©λ²
export function canadianToUs(canadian) {
    return roundTwoDecimals(canadian * exchangeRate);
}

// λλ²μ§Έ λ΄λ³΄λ΄κΈ° λ°©λ²
const usToCanadian = function(us) {
    return roundTwoDecimals(us / exchangeRate)
}
export { usToCanadian }
```
<br>

### Import

* μ¬λ¬ κ°μ²΄(Named Exports)λ₯Ό λΆλ¬μ¬ λλ ES6μ `Destructuring(κ΅¬μ‘°λΆν΄ν λΉ)` λ¬Έλ²μ μ¬μ©ν΄ νμν κ°μ²΄λ§ μ νμ μΌλ‘ μ μ­μμ μ¬μ©νκ±°λ, λͺ¨λ  κ°μ²΄μ λ³λͺμ λΆμ΄κ³  κ·Έ λ³λͺμ ν΅ν΄ μ κ·Όν  μλ μλ€.

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

### μ€νκ²°κ³Ό

```
50 Canadian dollars equals this amount of US dollars:
45.5
30 US dollars equals this amount of Canadian dollars:
32.97
```

<br>

### Single Object export/import

### Export

* CommonJsμμ λ΄λ³΄λΌ λ¨μΌ κ°μ²΄λ₯Ό module.exprotsλ³μμ ν λΉνλ λ°©μμ μ¬μ©νμΌλ ES6μμλ `export default` ν€μλλ₯Ό μ¬μ©ν΄ λͺμμ μΌλ‘ μ μΈ
* νλμ λͺ¨λμμ νλμ κ°μ²΄λ§ λ΄λ³΄λ΄κΈ° λλ¬Έμ μ΄λ₯Ό `Default Export`λΌκ³  ν¨

> μλ μμ λ λκ° ν¨μλ₯Ό κ°μ²΄λ‘ λ¬Άμ΄μ λ΄λ³΄λ΄κΈ°λ₯Ό ν μ½λμ΄λ€. μ΄λ¦μ΄ νμμκΈ° λλ¬Έμ λ³λ λ³μ ν λΉμ΄ μμ΄ λ°λ‘ κ°μ²΄λ₯Ό λ΄λ³΄λ΄κΈ° ν  μ μλ€. λ΄λ³΄λΌ λ μ΄λ€ μ΄λ¦λ μ§μ νμ§ μκΈ° λλ¬Έμ λΆλ¬μ¬ λλ μλ¬΄ μ΄λ¦μ΄λ μ¬μ©ν  μ μλ€.

### currency-object.js

```javascript
const exchangeRate = 0.91;

// λ΄λ³΄λ΄μ§ μμ
function roundTWoDecimals(amount) {
    return Math.round(amount * 100) / 100;
}

// λ΄λ³΄λ΄κΈ°
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

λ³μμ ν λΉνμ¬ λ΄λ³΄λ΄κΈ° νκ³  μΆλ€λ©΄ λ€μκ³Ό κ°μ΄ μμ±ν  μ μλ€.

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

* νλμ κ°μ²΄(Default Export)λ₯Ό λΆλ¬μ¬ λλ κ°λ¨νκ² `import` ν€μλλ₯Ό μ¬μ©ν΄ μλ¬΄ μ΄λ¦μ΄λ μνλ μ΄λ¦μ μ£Όκ³  ν΄λΉ κ°μ²΄λ₯Ό ν΅ν΄ μμ±μ μ κ·Όνλ©΄ λλ€.

### test-currendy-object.js

```javascript
import currency from "./currency-object"

console.log("50 Canadian dollars equals this amount of US dollars:")
console.log(currency.canadianToUs(50))

console.log("30 US dollars equals this amount of Canadian dollars:")
console.log(currency.usToCanadian(30))
```

### μ€νκ²°κ³Ό

```
50 Canadian dollars equals this amount of US dollars:
45.5
30 US dollars equals this amount of Canadian dollars:
32.97
```

<br>

> μ£Όμμ  : Babelμμ΄ μμνκ² Node.js μ΅μ  λ²μ μΌλ‘ ES λͺ¨λμ μ¬μ© μ import ν  λ .js νμ₯μλ₯Ό λΆμ¬μΌ νλ€.

### require()κ° μλλ° improtκ° μκΈ΄ μ΄μ 

* `require`μ `import`μ λν΄ λΉκ΅νκΈ° μν΄μλ μ°μ  CommonJSμ AMD(Asynchronous Module Dfinition), ES6 λ΄μ₯λͺ¨λκ³Ό κ°μ μλ°μ€ν¬λ¦½νΈμ λͺ¨λ μμ€νμ λν΄ μκ³  μμ΄μΌ νλ€.

* κΈ°μ‘΄μ μλ°μ€ν¬λ¦½νΈλ λͺ¨λμ΄λΌλ κ°λμ΄ λΆμ‘±νμ¬ κ° λͺ¨λ κ°μ μμ‘΄μ± μ²λ¦¬μ μ νμ΄ μμλ€.
* κ³ μ μ μΈ μΉ νλ‘μ νΈμμ μλ°μ€ν¬λ¦½νΈλ₯Ό μμνλ λ°©λ²μ HTML νμΌ λ΄λΆμ `<script>`νκ·Έλ₯Ό μ½μνμ¬ λͺ¨λμ λ‘λνλ€.
* <b>νμ§λ§ μ΄ λ°©μμ μλ°μ€ν¬λ¦½νΈ νμΌλΌλ¦¬ μλ‘ λͺ¨λμ κ³΅μ νλλ° μ μ½μ΄ μλ€λ λ¬Έμ κ° μλ€.</b>
* `<script>` νκ·Έλ‘Έ λ‘λλ λͺ¨λμ λͺ¨λ window κ°μ²΄μ μμ±μ΄κΈ° λλ¬Έμ μλ‘ λ€λ₯Έ νμΌμ μμΉνλ©΄μλ λͺ¨λ  κ°μ²΄λ₯Ό κ³΅μ ν  μ μκΈ° λλ¬Έ
<br><br>

* κ° μλ°μ€ν¬λ¦½νΈ νμΌμ΄ λλ¦½μ μΌλ‘ μ‘΄μ¬νμ§ λͺ»ν΄ λ°μνλ μ¬λ¬ λ¬Έμ λ€( λ€λ₯Έ νμΌμμ κ°μ μ΄λ¦μ λ³μλ₯Ό μ¬μ©νλ κ²½μ° λ±) λλμ νλμ λͺ¨λλ‘ κ΄λ¦¬νκΈ° μν λ€μν ν¨ν΄(Module Pattern, μ¦μ μ€ν ν¨μ λ±)μ μ¬μ©νμ¬ μμ‘΄μ±μ κ΄λ¦¬ν  μ λ°μ μμλ€.
* μ΄λ₯Ό ν΄κ²°νκΈ° μν μλ¨μΌλ‘ λͺ¨λμ΄λΌλ κ°λμ λμνμ¬ μ μν λ°©λ²μ΄ CommonJSμ AMDμ΄λ€.
* λ΄λΆμ μΌλ‘ λͺ¨λ μλ‘ κ°μ μμ‘΄μ±μ΄ μ§μλμ§ μλ μνλ‘ λ§λ€μ΄μ‘μΌλ©°, ES6μ μ΄λ₯΄λ¬ μΈμ΄ λ΄λΆμ μΌλ‘ μλ°μ€ν¬λ¦½νΈ λͺ¨λ μμ‘΄μ±μ μ§μνκ² λμλ€.(export, import)

<br>

### λͺ¨λ μ μ λ°©μμ νΌμ©

* ES6 λͺ¨λμ κΈ°λ³Έμ μΌλ‘ CommonJsμ AMD λͺ¨λμ νΌμ©ν΄μ μ¬μ©ν  μ μλ€.
* λͺ¨λμ κ°μ Έμ€λ λΆλΆμ `require()`μ `import`λ₯Ό κ°μ΄ μ¬μ©νλλΌλ λ¬Έμ μμ΄ λμνλ€.
* `import`λ ES6 λ¬Έλ²μ΄λΌ νμ¬ μ¬μ©λλ λΈλΌμ°μ μμλ μ§μνμ§ μμ§λ§, babelκ³Ό κ°μ νΈλμ€νμΌλ¬κ° ν΄κ²°ν΄μ€ μ μλ€.  