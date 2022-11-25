# 🌼[JavaScript] var, let, const

## 🌼 변수의 생성 과정

**① 선언 단계(Declaration phase)** : 변수 객체에 변수를 등록함

**② 초기화 단계(Initialization phase)** : 변수 객체에 등록된 변수를 메모리에 할당함. 이 단계에서 undefined로 초기화됨.

**③ 할당 단계(Assignment phase)** : undefined로 초기화된 변수에 실제값을 할당함

## 🌼 var

ES5까지는 변수를 var 키워드로만 선언을 할 수 있었다. var의 특징은 함수 레벨 스코프, var 키워드 생략 가능, 변수 중복 선언 허용, 변수 호이스팅이 가능하다.

### 함수 레벨 스코프

함수의 코드 블록만을 스코프로 인정한다. 따라서 전역 함수 외부에서 생성된 변수는 모두 전역 변수이다. for문의 변수 선언문에서 선언한 변수를 for문 바깥에서 참조할 수 있다.

### 호이스팅

호이스팅이란 모든 선언문이 해당 스코프의 선두로 옮겨진 것처럼 동작하는 특성이다. 따라서 자바스크립트는 모든 선언문이 선언되기 이전에 참조가 가능하다. 그렇기 때문에 다음과 같은 코드에서 undefined를 출력한다.

```jsx
console.log(foo); // ReferenceError를 예상하지만 undefined가 출력됨
var foo = 123;
```

var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어진다. 따라서 변수 선언문 이전에 변수에 접근하여도 변수객체에 변수가 존재하기 때문에 에러가 발생하지는 않지만 undefined를 반환한다.

### 전역 객체와 var

전역 객체(global object)는 모든 객체의 유일한 최상위 객체를 의미하며 일반적으로 brower-side에서는 window 객체, server-side(Node.js)에서는 global 객체를 의미한다. var키워드로 선언된 변수를 전역 변수로 사용하면 전역 객체의 프로퍼티가 된다.

```jsx
var foo = 123; // 전역 변수
console.log(window.foo); // 123
```

유효 범위가 넓어서 사용이 편리하다는 장점이 있지만, 유효범위가 넓기에 어디에서 어떻게 사용될 것인지 파악하기 힘들며 의도치 않게 변경될수도 있기 때문에 복잡성을 증가시킨다. 따라서 변수의 스코프는 좁을수록 좋다. 이러한 var의 단점을 보완하기 위해서 ES6에서는 let과 const 키워드를 도입했다.

## 🌼 let

대부분의 프로그래밍 언어는 블록 레벨 스코프를 따르지만 자바스크립트는 함수 레벨 스코프를 따른다. ES6는 블록 레벨 스코프를 따르는 변수를 선언하기 위해 let 키워드를 제공한다.

### 블록 레벨 스코프

모든 코드 블록 내에서 선언된 변수는 코드 블록 내에서만 유효하며 코드 블록 외부에서는 참조할 수 없다. 즉, 코드 블록 내부에서 선언된 변수는 지역 변수이다.

```jsx
let foo = 123; // 전역 변수
{
	let foo = 456; // 지역 변수
	let bar = 456; // 지역 변수
}
console.log(foo); // 1234
console.log(bar); // ReferenceError: bar is not defined
```

### 호이스팅

let 키워드로 선언된 변수는 선언문 이전에 참조하면 참조 에러가 발생한다. 스코프의 시작에서 변수의 선언까지 **일시적 사각지대(Temporal Dead Zone; TDZ)**에 빠지기 때문이다. 또한 선언 단계와 초기화 단계가 분리되어 진행되므로, 초기화 이전에 변수에 접근하려고 하면 참조 에러가 발생한다.

```jsx
console.log(foo); // ReferenceError: foo is not defined

let foo; // 변수 선언에서 초기화가 됨
console.log(foo); // undefined

foo = 1; // 할당문에서 할당 단계가 실행
console.log(foo); // 1
```

```jsx
let foo = 1; // 전역 변수
{
	console.log(foo); // ReferenceError: foo is not defined
	let foo = 2; // 지역 변수
}
```

### 전역 객체와 let

let 키워드로 선언된 변수를 전역 변수로 사용하는 경우, let 전역 변수는 전역 객체의 프로퍼티가 아니다. 즉, window.foo와 같이 접근할 수 없다. let 전역 변수는 보이지 않는 개념적인 블록 내에 존재하게 된다.

```jsx
let foo = 123; // 전역 변수
console.log(window.foo); // undefined
```

## 🌼 const

const는 상수를 위해 사용한다. 하지만 반드시 상수만을 위해 사용하지는 않는다. const의 특징은 let과 거의 동일하지만 const 고유의 특징들은 다음과 같다.

### 선언과 초기화

const는 반드시 선언과 동시에 할당이 이루어져야한다. 그렇지 않으면 문법 에러가 발생한다. 재할당이 금지되고, 재할당을 하게 되면 타입 에러가 발생한다.

```jsx
const FOO = 123;
FOO = 456; // TypeError: Assignment to constant variable

const BAR; // SyntaxError: Missing initializer in const declaration

{
	const FOOBAR = 10;
	console.log(FOOBAR); // 10
}
console.log(FOOBAR); // ReferenceError: FOOBAR is not defined
```

### const와 객체

const 변수의 타입이 객체일 경우, 객체에 대한 참조를 변경하지 못한다. 하지만 이때 객체의 속성은 보호되지 않는다. 따라서 재할당은 불가능하지만 할당된 객체의 내용(프로퍼티의 추가, 삭제, 변경)은 변경가능하다. 객체의 내용이 변경되더라도 객체 타입 변수에 할당된 주소값은 변경되지 않기 때문에 객체 타입 변수 선언에는 const를 사용하는 것이 좋다. 

```jsx
const user = { name: 'Lee' };
user.name = 'Kim';
console.log(user); // { name: 'Kim' }
```

### 📚 Reference

[https://poiemaweb.com/es6-block-scope](https://poiemaweb.com/es6-block-scope)

[https://poiemaweb.com/js-data-type-variable#24-변수-호이스팅variable-hoisting](https://poiemaweb.com/js-data-type-variable#24-%EB%B3%80%EC%88%98-%ED%98%B8%EC%9D%B4%EC%8A%A4%ED%8C%85variable-hoisting)