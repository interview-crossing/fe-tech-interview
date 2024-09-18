## 🧐 Additional Informations

#### 공통점

forEach, map공통점은 "배열을 이용한다"는 점이다. <br />
배열의 값을 조작해서 원하는 결과값을 도출하는데 의미가 있다.

<br />

#### 차이점

1. 새로운 배열을 반환하는 map()

forEach()가 배열 요소마다 한 번씩 주어진 함수를 실행하는 것과 달리, <br />
map()은 배열 내의 모든 요소 각각에 대하여 주어진 함수(콜백)를 호출한 결과를 모아 새로운 배열을 반환한다는 특징을 가지고 있다.

그리고, forEach()와 map()은 세 개의 인자를 가지고 호출된다.

```
1. currentValue (배열 원소의 값)
2. index (현재 요소의 인덱스)
3. array (현재 배열)
```

<br />

2. 리턴값을 보내지 않는 forEach()

forEach()는 문밖으로 리턴값을 받지 못한다.

```js
// forEach
let arr = [1, 2, 3, 4, 5];
let a = arr.forEach(function (value) {
  return value;
});
console.log(a); //undefined
```

```js
// map
let arr = [1, 2, 3, 4, 5];
let a = arr.map(function (value) {
  return value + 1;
});
console.log(a); // [2,3,4,5,6]
```

<br />
<hr />

References.

- [[자바스크립트 / Vanilla JS] forEach()와 map()의 차이점](https://growing-jiwoo.tistory.com/73)
