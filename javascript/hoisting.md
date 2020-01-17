# 🎍호이스팅

호이스팅이란 변수를 선언하고 초기화 했을 때 선언 부분이 최상단으로 끌어올려지는 현상

```javascript
console.log(zero); // 에러가 아니라 undefined
sayWow(); // 정상적으로 wow
function sayWow() {
  console.log("wow");
}
var zero = "zero";
```

sayWow처럼 함수 표현식이 아닌 함수 선언식일때 식 자체가 끌어올려짐

아래와 같음

```javascript
function sayWow() {
  console.log("wow");
}
var zero;
console.log(zero);
sayWow();
zero = "zero";
```

아래 같은 경우는 에러

```javascript
sayWow(); // (3)
sayYeah(); // (5) 여기서 대입되기 전에 호출해서 에러
var sayYeah = function() {
  // (1) 선언 (6) 대입
  console.log("yeah");
};
function sayWow() {
  // (2) 선언과 동시에 초기화(호이스팅)
  console.log("wow"); // (4)
}
```
