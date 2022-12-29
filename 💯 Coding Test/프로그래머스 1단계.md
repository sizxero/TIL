# 1️⃣ 프로그래머스 1단계

## 💯 .forEach() vs .map()

### .forEach()
배열 요소마다 한번씩 주어진 함수를 실행한다. 

### .map()
배열 내의 모든 요소 각각에 대하여 콜백 함수를 호출한 결과를 모아 새로운 배열을 반환한다.

```javascript
const arr = [1, 2, 3, 4, 5];

// forEach 사용
const mulArr = [];
arr.forEach(num => mulArr.push(num*3));

// map 사용
const mulArr = arr.map(num => num*3);

```


## 📚 References
https://dream-frontend.tistory.com/341