# 🏅 [JavaScript] 일급 객체

## 🏅 일급 객체

프로그래밍 언어에서 타입을 전달, 반환 및 할당할 수 있는 경우 해당 타입을 일급 객체로 간주한다. JavaScript는 함수형 프로그래밍으로, 함수를 인수로 받거나 함수를 반환하는 고차 함수를 만들 수 있다. 일급 객체는 다음 세 가지 조건을 만족하는데, 자바스크립트의 함수는 이 조건들을 모두 만족하기 때문에 일급 객체이다.

### ① 변수나 데이터에 할당할 수 있어야 함

```jsx
const func = function () {
	...
};
```

```jsx
const movie = {
	name: '아바타 2',
	director: '제임스 카메론',
	show: function() {
		console.log(`${this.name}의 감독은 ${this.director}`);
	}
}
```

### ② 객체의 인자로 넘길 수 있어야 함

```jsx
function showText(e) {
	...
}

$('form').on('submit', showText);
$('a').on('click', showText);
```

### ③ 리턴값으로 사용할 수 있어야 함

```jsx
function add(a) {
	return function(b) {
		return a + b;
	}
}

const add3 = add(3);
const add5 = add(5);

add3(2); // 5
add5(2); // 7
```

## 📚 References

[https://soeunlee.medium.com/javascript에서-왜-함수가-1급-객체일까요-cc6bd2a9ecac](https://soeunlee.medium.com/javascript%EC%97%90%EC%84%9C-%EC%99%9C-%ED%95%A8%EC%88%98%EA%B0%80-1%EA%B8%89-%EA%B0%9D%EC%B2%B4%EC%9D%BC%EA%B9%8C%EC%9A%94-cc6bd2a9ecac)