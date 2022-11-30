# 🖨️[JavaScript] Function

## 🖨️ 함수 선언식 (Function Declarations)

일반적인 프로그래밍 언어에서의 함수 선언과 비슷한 형식

함수명이 정의되어 있고, 별도의 할당 명령이 없다.

```jsx
function func() {
	...
}
```

## 🖨️ 함수 표현식 (Function Expressions)

유연한 자바스크립트 언어의 특징을 활용한 선언 방식

정의한 function을 별도의 변수에 할당한다.

```jsx
const func = function () {
	...
};
```

## 🖨️ 함수 선언식 vs 함수 표현식

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

### 📚 Reference

[https://joshua1988.github.io/web-development/javascript/function-expressions-vs-declarations/](https://joshua1988.github.io/web-development/javascript/function-expressions-vs-declarations/)

[https://taenami.tistory.com/86](https://taenami.tistory.com/86)