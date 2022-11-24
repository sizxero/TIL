# 🪝[React] Hook

## 🪝 Hook이란?

Hook은 **props, state, context, ref, lifecycle**과 같은 react 개념에 좀 더 직관적인 API를 제공한다. 또한 hook은 이 개념들을 엮기 위해 새로운 방법을 제공한다. Hook은 계층의 변화 없이 상태 관련 로직을 재사용할 수 있도록 도와준다. Hook을 통해 서로 비슷한 것을 하는 작은 함구의 묶음으로 컴포넌트를 나누는 방법을 사용할 수 있다. Hook은 함수 컴포넌트에서 React state와 생명주기 기능을 연동할 수 있게 해주는 함수이다. 

최상위에서만 Hook을 호출해야 한다. 반복문, 조건문, 중첩된 함수 내에서 Hook은 실행할 수 없다. react 함수 컴포넌트 내에서만 Hook을 호출해야 한다. 단, custom hook 내에서는 Hook을 호출할 수 있다.


## 🪝 useState

```jsx
const [count, setCount] = useState(0);
```

state는 함수형 컴포넌트 내에 다음과 같이 추가할 수 있는데, 이 state는 컴포넌트가 다시 렌더링 되어도 그대로 유지된다. useState는 현재의 state값과 이 값을 업데이트 하는 함수를 쌍으로 제공한다. 이 함수를 이벤트 핸들러나 다른 곳에서 호출함으로써 state를 변경가능하게 한다. 인자로 들어가는 값(위의 예시에서는 0)은 초기의 state값이다.

## 🪝 useEffect

컴포넌트 안에서 데이터를 가져오거나 구독하고, DOM을 직접 조작하는 작업을 side effects라고 한다. 이것은 다른 컴포넌트에 영향을 줄 수도 있고, 랜더링 과정에서는 구현할 수 없는 작업이기 때문이다. useEffect는 이러한 side effects를 함수 컴포넌트 내에서 할 수 있도록 하는 hook이다. React class의 componentDidMount, componentDidUpdate, componentWillUnmount와 같은 목적으로 제공되지만 하나의 API로 통합된 것이다.


useEffect를 사용하면 React는 DOM을 바꾼 뒤에 effect 함수를 실행할 것이다. effects는 컴포넌트 내에 선언되어 있기 때문에 props와 state에 접근할 수 있다. effect는 해제할 필요가 있다면 해제하는 함수를 반환할 수 있다.

useEffect는 우리가 react에게 컴포넌트가 렌더링 이후에 어떤 일을 수행해야 하는지를 말한다. 첫번째 렌더링과 이후의 모든 update에서 수행이 된다. effect가 수행되는 시점에서 이미 DOM이 업데이트 되었음을 보장한다.

effect에 정리가 필요한 경우에는 함수를 반환한다. React는 컴포넌트가 마운트 해제될 때 정리를 실행한다. effect는 랜더링이 실행될 때마다 실행되기 때문에, React가 다음 차례의 effect를 실행하기 전에 이전의 렌더링에서 파생된 effect를 정리할 필요가 있다.

```jsx
useEffect(() => {
	function handleStatusChange(status) {
		setIsOnline(status.isOnline);
	}
	ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
	return() => {
		ChatAPI.unsubscribeToFriendStatus(props.friend.id, handleStatusChange);
	};
});
```

```jsx
componentDidMount() {
    ChatAPI.subscribeToFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }

  componentDidUpdate(prevProps) {
    // 이전 friend.id에서 구독을 해지합니다.
    ChatAPI.unsubscribeFromFriendStatus(
      prevProps.friend.id,
      this.handleStatusChange
    );
    // 다음 friend.id를 구독합니다.
    ChatAPI.subscribeToFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }

  componentWillUnmount() {
    ChatAPI.unsubscribeFromFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }
```

```jsx
// { friend: { id: 100 } } state로 마운트
ChatAPI.subscribeToFriendStatus(100, handleStatusChange);   // 첫 번째 effect

// { friend: { id: 200 } } state로 업데이트
ChatAPI.unsubscribeToFriendStatus(100, handleStatusChange); // 이전 effect 정리
ChatAPI.subscribeToFriendStatus(200, handleStatusChange);   // 다음 effect

// { friend: { id: 300 } } state로 업데이트
ChatAPI.unsubscribeToFriendStatus(200, handleStatusChange); // 이전 effect 정리
ChatAPI.subscribeToFriendStatus(300, handleStatusChange);   // 다음 effect

// 마운트 해제
ChatAPI.unsubscribeToFriendStatus(300, handleStatusChange); // 마지막 effect 정리
```

반환하지 않는 경우는 이렇게 선언한다.

```jsx
useEffect(() => {
	document.title = `You clicked ${count} times`;
});
```

만약 effect를 건너뛰고 싶다면 다음과 같이 선언한다. count의 값이 변할 때만 랜더링이 된다. 클래스형 컴포넌트에서 저런 요구사항은 흔하므로, useEffect에 이미 내재되어 있다. 만약 effect 실행과 정리를 마운트와 마운트 해제시에 딱 한번씩만 실행하고 싶다면, 빈 배열을 두 번째 인수로 넘기면 된다.

```jsx
useEffect(() => {
	document.title = `You clicked ${count} times`;
}, [count]);
```

```jsx
componentDidUpdate(prevProps, prevState) {
  if (prevState.count !== this.state.count) {
    document.title = `You clicked ${this.state.count} times`;
  }
}
```


### 📚 Reference

[https://ko.reactjs.org/docs/hooks-intro.html](https://ko.reactjs.org/docs/hooks-intro.html)