# ❓ [JavaScript] 물음표

## ❓Optional Chaining (?.)

객체의 속성에 접근하는 경우에 사용한다. ?. 연산자의 왼쪽이 null이거나 undefined일 때, undefined를 남긴다. 따라서 중첩된 객체 자료에서 데이터를 뽑을 때 reference 오류 없이 안전하게 뽑을 수 있다.

``` jsx
var user = {
    name: 'kim',
    // age: {value : 20 }
};

console.log(user.age.value);  // Uncaught TypeError
console.log(user.age?.value); // undefined

```


## ❓Null 병합 연산자 (??)

## 📚 References

[https://www.youtube.com/watch?v=WHUvtiKy_pg](https://www.youtube.com/watch?v=WHUvtiKy_pg)

[https://developer-talk.tistory.com/300](https://developer-talk.tistory.com/300)