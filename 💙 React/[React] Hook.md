# ๐ช[React] Hook

## ๐ช Hook์ด๋?

Hook์ **props, state, context, ref, lifecycle**๊ณผ ๊ฐ์ react ๊ฐ๋์ ์ข ๋ ์ง๊ด์ ์ธ API๋ฅผ ์ ๊ณตํ๋ค. ๋ํ hook์ ์ด ๊ฐ๋๋ค์ ์ฎ๊ธฐ ์ํด ์๋ก์ด ๋ฐฉ๋ฒ์ ์ ๊ณตํ๋ค. Hook์ ๊ณ์ธต์ ๋ณํ ์์ด ์ํ ๊ด๋ จ ๋ก์ง์ ์ฌ์ฌ์ฉํ  ์ ์๋๋ก ๋์์ค๋ค. Hook์ ํตํด ์๋ก ๋น์ทํ ๊ฒ์ ํ๋ ์์ ํจ๊ตฌ์ ๋ฌถ์์ผ๋ก ์ปดํฌ๋ํธ๋ฅผ ๋๋๋ ๋ฐฉ๋ฒ์ ์ฌ์ฉํ  ์ ์๋ค. Hook์ ํจ์ ์ปดํฌ๋ํธ์์ React state์ ์๋ช์ฃผ๊ธฐ ๊ธฐ๋ฅ์ ์ฐ๋ํ  ์ ์๊ฒ ํด์ฃผ๋ ํจ์์ด๋ค. 

์ต์์์์๋ง Hook์ ํธ์ถํด์ผ ํ๋ค. ๋ฐ๋ณต๋ฌธ, ์กฐ๊ฑด๋ฌธ, ์ค์ฒฉ๋ ํจ์ ๋ด์์ Hook์ ์คํํ  ์ ์๋ค. react ํจ์ ์ปดํฌ๋ํธ ๋ด์์๋ง Hook์ ํธ์ถํด์ผ ํ๋ค. ๋จ, custom hook ๋ด์์๋ Hook์ ํธ์ถํ  ์ ์๋ค.


## ๐ช useState

```jsx
const [count, setCount] = useState(0);
```

state๋ ํจ์ํ ์ปดํฌ๋ํธ ๋ด์ ๋ค์๊ณผ ๊ฐ์ด ์ถ๊ฐํ  ์ ์๋๋ฐ, ์ด state๋ ์ปดํฌ๋ํธ๊ฐ ๋ค์ ๋ ๋๋ง ๋์ด๋ ๊ทธ๋๋ก ์ ์ง๋๋ค. useState๋ ํ์ฌ์ state๊ฐ๊ณผ ์ด ๊ฐ์ ์๋ฐ์ดํธ ํ๋ ํจ์๋ฅผ ์์ผ๋ก ์ ๊ณตํ๋ค. ์ด ํจ์๋ฅผ ์ด๋ฒคํธ ํธ๋ค๋ฌ๋ ๋ค๋ฅธ ๊ณณ์์ ํธ์ถํจ์ผ๋ก์จ state๋ฅผ ๋ณ๊ฒฝ๊ฐ๋ฅํ๊ฒ ํ๋ค. ์ธ์๋ก ๋ค์ด๊ฐ๋ ๊ฐ(์์ ์์์์๋ 0)์ ์ด๊ธฐ์ state๊ฐ์ด๋ค.

## ๐ช useEffect

์ปดํฌ๋ํธ ์์์ ๋ฐ์ดํฐ๋ฅผ ๊ฐ์ ธ์ค๊ฑฐ๋ ๊ตฌ๋ํ๊ณ , DOM์ ์ง์  ์กฐ์ํ๋ ์์์ side effects๋ผ๊ณ  ํ๋ค. ์ด๊ฒ์ ๋ค๋ฅธ ์ปดํฌ๋ํธ์ ์ํฅ์ ์ค ์๋ ์๊ณ , ๋๋๋ง ๊ณผ์ ์์๋ ๊ตฌํํ  ์ ์๋ ์์์ด๊ธฐ ๋๋ฌธ์ด๋ค. useEffect๋ ์ด๋ฌํ side effects๋ฅผ ํจ์ ์ปดํฌ๋ํธ ๋ด์์ ํ  ์ ์๋๋ก ํ๋ hook์ด๋ค. React class์ componentDidMount, componentDidUpdate, componentWillUnmount์ ๊ฐ์ ๋ชฉ์ ์ผ๋ก ์ ๊ณต๋์ง๋ง ํ๋์ API๋ก ํตํฉ๋ ๊ฒ์ด๋ค.


useEffect๋ฅผ ์ฌ์ฉํ๋ฉด React๋ DOM์ ๋ฐ๊พผ ๋ค์ effect ํจ์๋ฅผ ์คํํ  ๊ฒ์ด๋ค. effects๋ ์ปดํฌ๋ํธ ๋ด์ ์ ์ธ๋์ด ์๊ธฐ ๋๋ฌธ์ props์ state์ ์ ๊ทผํ  ์ ์๋ค. effect๋ ํด์ ํ  ํ์๊ฐ ์๋ค๋ฉด ํด์ ํ๋ ํจ์๋ฅผ ๋ฐํํ  ์ ์๋ค.

useEffect๋ ์ฐ๋ฆฌ๊ฐ react์๊ฒ ์ปดํฌ๋ํธ๊ฐ ๋ ๋๋ง ์ดํ์ ์ด๋ค ์ผ์ ์ํํด์ผ ํ๋์ง๋ฅผ ๋งํ๋ค. ์ฒซ๋ฒ์งธ ๋ ๋๋ง๊ณผ ์ดํ์ ๋ชจ๋  update์์ ์ํ์ด ๋๋ค. effect๊ฐ ์ํ๋๋ ์์ ์์ ์ด๋ฏธ DOM์ด ์๋ฐ์ดํธ ๋์์์ ๋ณด์ฅํ๋ค.

effect์ ์ ๋ฆฌ๊ฐ ํ์ํ ๊ฒฝ์ฐ์๋ ํจ์๋ฅผ ๋ฐํํ๋ค. React๋ ์ปดํฌ๋ํธ๊ฐ ๋ง์ดํธ ํด์ ๋  ๋ ์ ๋ฆฌ๋ฅผ ์คํํ๋ค. effect๋ ๋๋๋ง์ด ์คํ๋  ๋๋ง๋ค ์คํ๋๊ธฐ ๋๋ฌธ์, React๊ฐ ๋ค์ ์ฐจ๋ก์ effect๋ฅผ ์คํํ๊ธฐ ์ ์ ์ด์ ์ ๋ ๋๋ง์์ ํ์๋ effect๋ฅผ ์ ๋ฆฌํ  ํ์๊ฐ ์๋ค.

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
    // ์ด์  friend.id์์ ๊ตฌ๋์ ํด์งํฉ๋๋ค.
    ChatAPI.unsubscribeFromFriendStatus(
      prevProps.friend.id,
      this.handleStatusChange
    );
    // ๋ค์ friend.id๋ฅผ ๊ตฌ๋ํฉ๋๋ค.
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
// { friend: { id: 100 } } state๋ก ๋ง์ดํธ
ChatAPI.subscribeToFriendStatus(100, handleStatusChange);   // ์ฒซ ๋ฒ์งธ effect

// { friend: { id: 200 } } state๋ก ์๋ฐ์ดํธ
ChatAPI.unsubscribeToFriendStatus(100, handleStatusChange); // ์ด์  effect ์ ๋ฆฌ
ChatAPI.subscribeToFriendStatus(200, handleStatusChange);   // ๋ค์ effect

// { friend: { id: 300 } } state๋ก ์๋ฐ์ดํธ
ChatAPI.unsubscribeToFriendStatus(200, handleStatusChange); // ์ด์  effect ์ ๋ฆฌ
ChatAPI.subscribeToFriendStatus(300, handleStatusChange);   // ๋ค์ effect

// ๋ง์ดํธ ํด์ 
ChatAPI.unsubscribeToFriendStatus(300, handleStatusChange); // ๋ง์ง๋ง effect ์ ๋ฆฌ
```

๋ฐํํ์ง ์๋ ๊ฒฝ์ฐ๋ ์ด๋ ๊ฒ ์ ์ธํ๋ค.

```jsx
useEffect(() => {
	document.title = `You clicked ${count} times`;
});
```

๋ง์ฝ effect๋ฅผ ๊ฑด๋๋ฐ๊ณ  ์ถ๋ค๋ฉด ๋ค์๊ณผ ๊ฐ์ด ์ ์ธํ๋ค. count์ ๊ฐ์ด ๋ณํ  ๋๋ง ๋๋๋ง์ด ๋๋ค. ํด๋์คํ ์ปดํฌ๋ํธ์์ ์ ๋ฐ ์๊ตฌ์ฌํญ์ ํํ๋ฏ๋ก, useEffect์ ์ด๋ฏธ ๋ด์ฌ๋์ด ์๋ค. ๋ง์ฝ effect ์คํ๊ณผ ์ ๋ฆฌ๋ฅผ ๋ง์ดํธ์ ๋ง์ดํธ ํด์ ์์ ๋ฑ ํ๋ฒ์ฉ๋ง ์คํํ๊ณ  ์ถ๋ค๋ฉด, ๋น ๋ฐฐ์ด์ ๋ ๋ฒ์งธ ์ธ์๋ก ๋๊ธฐ๋ฉด ๋๋ค.

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


### ๐ Reference

[https://ko.reactjs.org/docs/hooks-intro.html](https://ko.reactjs.org/docs/hooks-intro.html)