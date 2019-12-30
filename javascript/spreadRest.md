# 🎞Rest 파라미터, spread 연산자

## Rest 파라미터

Rest 파라미터는 Spread 연산자(...)를 사용하여 함수의 파라미터를 작성한 형태

```javascript
function foo(...rest) {
  console.log(Array.isArray(rest)); // true
  console.log(rest); // [ 1, 2, 3, 4, 5 ]
}
foo(1, 2, 3, 4, 5);
```

- rest 파라미터는 항상 제일 마지작 파라미터로 있어야 한다.

## spread 연산자

Spread 연산자는 연산자의 대상 배열 또는 이터러블(iterable)을 "개별" 요소로 분리한다.

```javascript
// 배열
console.log(...[1, 2, 3]); // -> 1, 2, 3

// 문자열
console.log(..."Helllo"); // H e l l l o

// Map과 Set
console.log(
  ...new Map([
    ["a", "1"],
    ["b", "2"]
  ])
); // [ 'a', '1' ] [ 'b', '2' ]
console.log(...new Set([1, 2, 3])); // 1 2 3
```

함수의 파라미터로 사용할 수 있다

```javascript
// ES6
function foo(x, y, z) {
  console.log(x); // 1
  console.log(y); // 2
  console.log(z); // 3
}
const arr = [1, 2, 3];
foo(...arr); // Array를 받아서 각 매개변수로 전달되었다.
```

## rest와 spread

```javascript
//Rest
function foo(param, ...rest) {
  console.log(param); // 1
  console.log(rest); // [ 2, 3 ]
}
foo(1, 2, 3);

//Spread호출
function bar(x, y, z) {
  console.log(x); // 1
  console.log(y); // 2
  console.log(z); // 3
}
bar(...[1, 2, 3]);
```
