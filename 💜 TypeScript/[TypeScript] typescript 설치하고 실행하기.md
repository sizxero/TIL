# 🧵 [TypeScript] typescript 설치하고 실행하기

## 🧵 패키지 설치

### ① typescript

npm i -g typescript

### ② ts-node

npm i -g ts-node



![image](https://user-images.githubusercontent.com/51533341/209078015-75f5578e-4514-4501-b981-cfeda371d4e9.png)


*한꺼번에 설치할 시 : npm i -g typescript ts-node

## 🧵 실행

```jsx
// 1222_01.ts
let hello: string = "hello TS";
console.log(hello);
```

### ① 파일 직접 실행

ts-node <파일명> 

![image](https://user-images.githubusercontent.com/51533341/209078098-b0e6c804-5312-45dd-8c0b-ce03f5ef3447.png)


### ② 파일 컴파일 실행

**>tsc <파일명>**

컴파일된 js 파일이 생성된다.

![image](https://user-images.githubusercontent.com/51533341/209078195-431e3293-ad66-4ff5-b98f-7ba524195141.png)


```jsx
// 1222_01.js
var hello = "hello TS";
console.log(hello);
```

**>node <파일명>**

![image](https://user-images.githubusercontent.com/51533341/209078270-5be9f6e0-f6ca-43a1-8045-23bf74a88887.png)


## 📚 References

[https://juntcom.tistory.com/157](https://juntcom.tistory.com/157)
