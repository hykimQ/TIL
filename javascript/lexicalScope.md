# Lexical Scope

#### 함수를 선언할 때 함수 내부의 변수는 자기 scope로부터 가장 가까아누 scope에 있는 변수를 참조

```javascript
var name = "one";
function log() {
  console.log(name);
}

function wrapper() {
  var name = "two";
  log();
}
wrapper(); // one
```

- log 함수의 name 변수는 log함수가 선언 될 때 가장 가까운 전역변수 name 참조
- wrapper함수를 호출 시 wrapper안의 지역변수 name을 참조하지 않음 (선언 시점에 log함수의 name이 전역변수를 참조)
