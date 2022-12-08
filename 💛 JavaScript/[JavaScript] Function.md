## 🖨 함수 선언식 (Function Declarations)

일반적인 프로그래밍 언어에서의 함수 선언과 비슷한 형식

함수명이 정의되어 있고, 별도의 할당 명령이 없다.

```jsx
function func() {
	...
}
```

## 🖨 함수 표현식 (Function Expressions)

유연한 자바스크립트 언어의 특징을 활용한 선언 방식

정의한 function을 별도의 변수에 할당한다.

```jsx
const func = function () {
	...
};
```

## 🖨 함수 선언식 vs 함수 표현식

*함수 선언식은 호이스팅에 영향을 받지만, 함수 표현식은 호이스팅에 영향을 받지 않음*

함수 선언식은 함수 전체를 호이스팅하며, 정의된 범위의 맨 위로 호이스팅 되서 선언 전에 함수를 사용할 수 있다. 반면 함수 표현식은 별도의 변수에 할당하게 되어서 변수의 선언부만 호이스팅하게 된다.

```jsx
sum(50, 50);   // 100
minus(50, 50); // Uncaught TypeError: minus is not a function

// 함수 선언식
function sum(a, b) {
	return a + b;
}

// 함수 표현식
var minus = function(a, b) {
	return a - b;
}
```

위의 코드에서 호이스팅이 마치게 되면 다음과 같이 표현된다.

```jsx
// 함수 표현식
function sum(a, b) {
	return a + b;
}

// 함수 표현식: 선언부 호이스팅
var minus;

sum(50, 50);   // 100
minus(50, 50); // Uncaught TypeError: minus is not a function

// 함수 표현식: 할당부
function (a, b) {
	return a - b;
}
```

함수 표현식을  코드를 호출하는 부분 위에 작성하면 에러 없이 정상적으로 출력된다. 함수 선언식으로 작성한 함수는 함수 전체가 호이스팅 되기 때문에 전역적으로 선언 시 중복적으로 동명의 함수를 쓰게 될 때 원치 않는 결과가 나올 수 있다. 따라서 함수 표현식으로 작성하여 이를 방지하는 것이 좋다.

## 🖨 화살표 함수

자바스크립트는 함수를 1급 객체로 취급하고 값으로 대입 가능하기 때문에 함수의 인자값으로 함수를 넘긴다. 그리고 함수 내부에서 그 인자값으로 들어온 함수를 호출하는 **콜백 함수**를 코드 작성 시에 자주 이용하기 때문에 함수를 작성해야 할 일이 많다. 특히 콜백 함수를 인자값으로 넘길 때는 한 번만 사용될 것이기 때문에 익명함수를 작성해야 하는데, 그 익명함수를 간단하게 작성하도록 해주는 것이 화살표 함수이다.

```jsx
const add = function (a, b) {
	return a+b;
}

// 화살표 함수로 축약
const add = (a, b) => a+b;
```

화살표 함수와 일반 함수의 큰 차이점은 this이다.

일반 함수의 this는 함수가 쓰인 위치에 따라서 내부의 this값이 변하지만 화살표 함수는 어디에서든지 this값을 변화시키지 않는다. 화살표 함수에서의 this는 자기가 정의된 스코프에 존재하는 this를 가르킨다. 그렇기 때문에 객체의 메소드를 화살표 함수로 정의하면 자신의 상위에 있는 스코프의 this를 가르키기 때문에 처음부터 this가 window이다.

```jsx
var obj1 = {
    name: 'obj1',
    func1 : function(){ console.log(this.name) }
}
var obj2 = {
    name: 'obj2',
    func2 : () => console.log(this.name) 
}

obj1.func1();  // obj1
obj2.func2();  // undefined
```

따라서 화살표 함수는 일반 함수를 대체할 수 있는 문법이 아니다.

## 📚 Reference

[https://joshua1988.github.io/web-development/javascript/function-expressions-vs-declarations/](https://joshua1988.github.io/web-development/javascript/function-expressions-vs-declarations/)

[https://taenami.tistory.com/86](https://taenami.tistory.com/86)

[https://pgh268400.tistory.com/490](https://pgh268400.tistory.com/490)

[https://sangjuntech.tistory.com/24](https://sangjuntech.tistory.com/24)

[https://codingapple.com/unit/es6-3-arrow-function-why/](https://codingapple.com/unit/es6-3-arrow-function-why/)