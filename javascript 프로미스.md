## javascript 동기적 처리와 비동기적 처리



## 1. 동기적 처리와 비동기적 처리

- Syncronous(동기): 요청을 보낸 후, 해당 요청의 응답을 받아야 다음 동작을 실행( 코드를 한줄 실행 완료 후, 다음 줄 실행)
- Asynchronous(비동기) : 요청을 보낸 후, 응답과 관계없이 다음 동작을 실행( 코드를 한줄 실행 후, 완료와 상관없이 다음 줄 실행)



### 비동기적 처리의 이해

- 대부분의 프로그래밍 언어는 동기적 처리를 지향함
- 하지만, javascript 의 경우는 실행이 오래 걸리는 동작의 경우, 이를 온전히 기다릴 필요 없이 다음 작업 실행이 가능하도록, 비동기적인 처리도 가능하도록 되어있음.
- 따라서, javascript는 다른 언어와 마찬가치로 동기적 처리가 기본이지만, 일부 기능은 비동기적으로 처리가 가능하도록 관련 기능을 추가로 제공하고 있다고 이해하면 좋음



### 주요 비동기적 처리

오래 걸리는 기능은 비동기적으로 처리됨

- Rest API 요청
- 파일/데이터베이스 처리
- 타이머, 암호화/복호화 등



### 비동기 처리 예(setTimeout 함수)



setTimeout()



```javascript
SetTime(function, milliseconds)
```

- miliseconds: ms만큼 기다리기
- fucntion: milliseconds에서 설정한 ms만큼 기다린 후, 호출할 함수



코드 예

```javascript
console.log("꼼꼼하고, 선명하고, 바로 활용하는 멋쟁이 사자처럼")
setTime(() => {
	console.log("나도 할 수 있다");
}, 3000);
console.log("jin")
```



### 비동기 처리의 문제점

예를 들어, Rest API를 호출해서 결과값을 받아서, 이를 기반으로 코드를 실행하는 경우를 생각해보기로 함

해당 함수 호출 후, 결과값을 받지 않은 채로, 다음 코드가 실행되면, 전체 코드 실행에 문제가 됨

> Vanilla javascript에서 Rest API 호출을 위해 XMLHttpRequest 라는 기술(함수)을 제공하지만, 호환성 이슈가 있으므로, 최신 기술이고 보편적으로 쓰이는 axios를 사용하는 것이 최근 추세임



### 비동기 처리의 문제점을 해결할 수 있는 콜백함수(Callback Fucntion)

#### 예제코드

```javascript
function func1() {
	setTimeout(() => {
		console.log(1);
	}, 1000);
}
function func2() {
	console.log(2);
}
func1();
func1();
```



### 콜백 함수 설정

- 자바스크립트에서 함수는 first-class function
  - first-class function은 파이썬 백엔드 과정에서 설명함
    - 함수 자체를 변수에 저장 가능
    - 함수의 인자에 다른 함수를 인수로 전달 가능
    - 함수의 반환 값(return 값)으로 함수를 전달 가능

```javascript
function func1(callback){
	setTimeout(() => {
		console.log("func1");
		callback();
	}, 1000);
}

function func2() {
	console.log("func2");
}
func1(func2)
```



### 콜백지옥

```javascript
function func1(callback) {
	setTimeout(() => {
		console.log("1");
		setTimeout(() => {
			console.log("2");
			setTimeout(() => {
				callback();
			}, 500);
		}, 500);
	}, 500);
}

function func2() {
	console.log("3");
}
func1(func2);
```



## 2.promise

ES6에서 공식적으로 추가된 문법으로, 비동기 처리를 위한 콜백함수의 단점을 극복하기 위해 제안됨



1. new로 Promise 객체 생성
2. Promise 객체는 executor 라는 함수가 자동으로 실행되고, executor라는 함수는 resolev와 reject라는 두 개의 함수를 인자로 받아서 비동기 처리 함수를 실행
3.  excoutor 를 통해 비동기 처리 함수를 실행 완료 후, 해당 작업이 성공이면 resolve, 실패면 reject 함수를 호출

```javascript
//promise 객체 생성
const promise = new Promise((resolve, reject) => {
	// 비동기 작업 수행
	setTimteout(() => {
		let num = 10;
		if (num >= 11) {
			/* 비동기 작업 성공 */
			resolve(num);
		} else {
			/* 비동기 작업 실패 */
			reject("error");
		}
	}, 1000);
});
```





### Promise 의 3가지 상태 (states)

위 코드에서 promise 변수(즉, Promise 객체)는 다음과 같이 3가지 상태를 가질 수 있음

- Pending(대기): 비동기 처리가 아직 실행되지 않은(초기) 상태
- Fulfilled(이행): 비동기 처리가 성공적으로 완료된 상태
- Rejected(실패): 비동기 처리가 실패한 상태



### then 메서드

위 코드에서 작업 성공 또는 실패시, 수행할 작업을 정의하고, promise 코드를 실행해주는 메서드

- 두 콜백 함수를 인자로 받음
  - successCallack: 작업 성공 시의 실행 함수
  - failureCallback: 작업 실패 시의 실행 함수

```javascript
promise.then(succesCallback, failureCallback)
```



예제 코드: 다음 num >= 11을 num >=5로 변경해서, 동작을 확인해보세요

```javascript
//Promise 객체 생성
const promise = new Promise((resolve, reject) => {
	//비동기 작업 수행
	setTimeout(() => {
		let num = 10;
		if (num >= 11) {
			/* 비동기 작업 성공 */
			resolve(num);
		} else {
			reject("error");
		}
	}, 1000);
});

promise.then(
	(num) => {
		console.log("success", num);
	},
	(err) => {
		console.log(err);
	}
);
```





then 메서드에 하나의 함수만 선언할 경우, 이는 successCallback 동작만 선언한 셈임

```javascript
//Promise 객체 생성
const promise = new Promise((resolve, reject) => {
	//비동기 작업 수행
	setTimeout(() => {
		let num = 10;
		if (num >= 11) {
			/* 비동기 작업 성공 */
			resolve(num);
		} else {
			/* 비동기 작업 실패 */
			reject("error");
		}
	}, 1000;
});

promise.then(
	(num) => {
		console.log("success", num);
	}
);
```



### 콜백 지옥과 Promise

```javascript
//promiser 객체 생성
const promise = new Promise((resolve, rejucet) => {
	//비동기 작업 수행
	setTimeout(() => {
		let num = 10;
		if (num >= 11) {
			/* 비동기 작업 성공 */
			resolve(num);
		} else {
			/* 비동기 작업 실패 */
			reject("error");
		}
	}, 1000);
});

// 실행 순서에 맞춰줄 필요가 있을 경우, then을 이어서 작성해줄 수 있음 (콜백지옥에서 해방됨)

promise.then (
	(num) => {
		console.log("success", num);
	}
).then (
	() => {
		console.log("succees", num);
	}
)
```



### catch 메서도

- 실행 중, 예외상황을 처리함
- failureCallback 가 정의되어 있지 않을 경우, reject 시에도 catch 메서드를 호출함

```javascript
//promise 객체 생성
const promise = new Promise(resolve, reject) => {
	//비동기 작업 수행
	setTimeout(() => {
		let num = 10;
		if(num >= 11) {
			/* 비동기 작업 성공 */
			resolve(num);
		} else {
			/* 비동기 작업 실패 */
			reject("this is an error");
		}
	},1000);
});

promise
	.then((num) => {
		console.log("success" num);
	})
	.catch(error) => {
		console.log(error);
	});
```



chaning

- then 메서드를 연결해서, 순차적으로 실행되어야할 코드를 연결할 수 있음
- then과 catch메서드도 함께 연결해서 실행가능함

```javascript
// promiser 객체 생성
const promise = new Promise(resolve, reject) => {
	console.log("start");
	resolve();
});

promise
	.then(() => {
		console.log("succes 1");
		throw new Error("error");
	})
	.catch((err) => {
		console.log(err);
	})
	.then(() => {
		console.log("success 2");
	});
```



### 참고:throw

- 사용자 정의 예외를 던질 때 사용
  - catch 블록이 있으면 catch 블록을 전달되고, 그렇지 않으면 프로그램을 종료함
- 보통 다음과 같은 구문으로 사용됨(Error 클래스의 객체를 만들어서, 전달함)

```javascript
throw ne Erroe('에러메세지')
```



chainig 과 catch

- 일반적으로 catch를 chaining 맨 마지막에 추가해서, 전체 코드의 에러 케이서를 간결히 핸들링



```javascript
//Promise 객체 생성
const promise = new Promise((resolve, reject) => {
	console.log("start");
	resolve(1);
});

promise
	.then((num) => {
		console.log("success1");
	})
	.then((num) => {
		console.log("success2");
		throw new Error("error");
	})
	.then((num) => {
		console.log("success3");
	});
```



finally

finally()는 promise 가 resolve 되든 reject되든 마지막에 해당함수를 실행함

```javascript
//promiser 객체 생성
const promise = new Promise(resolve, reject) => {
	//비동기 작업 수행
	setTimeout(() => {
		let num =10;
		if (num >= 9) {
			/* 비동기 작업 성공 */
			reject("this is an error");
		}
	}, 500);
});

promise
	.then((num) => {
		console.log("succes1", num);
		return2; /* return 값이 다음 then의 인자로 넘겨짐 */
	})
	.then((num) => {
		console.log("succes2",num);
	})
	.finally(() => {
		console.log("finally");
	});
```



### Promise.all

- 동기화 처리할 Promise를 묶어서 한번에 실행
- 즉 여러 함수가 다 실행이 완료된 후에, then 구문을 실행함

```javascript
const promise1 = new Promise((resovle, reject) => {
	setTimeout(() => resolve("100ms"), 100);
});

conset promise2 = new Promise((resolve, reject) => 
	setTimeout(() => resolve("500ms"), 500);
});

Promise.all([promise1, promise2]).then((data) => {
	console.log(data);
});
```



### Promise.race

- 여러 함수 중, 제일 빠르게 실행 완료된 함수만 then 구문을 실행함

```javascript
const promise1 = new Promise((resolve, reject) => {
	setTimeout(() => resolve("100ms"), 100);
});

const promise2 = new Promise((resolve, reject) => {
	setTimeout(() => resolve("500ms"), 500);
});

Promise.race([promise1, promise2]).then(data) => {
	console.log(data);
});
```

















