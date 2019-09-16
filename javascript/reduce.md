# reduce()

#### 배열의 각 요소에 대해 주어진 리듀서 함수를 실행하고, 하나의 결과값을 반환

네개의 인자

1. 누산기 accumulator (acc)
2. 현재 값 (cur)
3. 현재 인덱스 (idx)
4. 원본 배열 (src)

reduce 함수 호출에서 initialValue가 있으면 accumulator은 initialValue와 같고 현재값은 배열의 첫번째 값과 같다.
reduce 함수 호출에서 initialValue가 없으면 accumulator은 배열의 첫번째 값과 같고 현재값은 배열의 두번째 값과 같다.

> reduce 함수 호출에서 initialValue가 있으면 인덱스는 1에서 시작하고 initialValue가 없으면 인덱스는 0에서 시작

initialValue가 없으면 여러값이 결과로 나올 수 있어 보통 initialValue가 있는게 더 안전하다.

배열의 모든 값 합산

```javascript
var total = [0, 1, 2, 3].reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  0
);
```

객체 배열에서의 값 합산

```javascript
var initialValue = 0;
var sum = [{ x: 1 }, { x: 2 }, { x: 3 }].reduce(
  (accumulator, currentValue) => accumulator + currentValue.x,
  initialValue
);

console.log(sum); // logs 6
```

함수 구성을 위한 파이프 함수

```javascript
// Building-blocks to use for composition
const double = x => x + x;
const triple = x => 3 * x;
const quadruple = x => 4 * x;

// Function composition enabling pipe functionality
const pipe = (...functions) => input =>
  functions.reduce((acc, fn) => fn(acc), input);

// Composed functions for multiplication of specific values
const multiply6 = pipe(
  double,
  triple
);
const multiply9 = pipe(
  triple,
  triple
);
const multiply16 = pipe(
  quadruple,
  quadruple
);
const multiply24 = pipe(
  double,
  triple,
  quadruple
);

// Usage
multiply6(6); // 36
multiply9(9); // 81
multiply16(16); // 256
multiply24(10); // 240
```

[https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)
