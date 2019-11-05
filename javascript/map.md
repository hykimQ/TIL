# Map

객체는 키-값 쌍을 저장하며 각 쌍의 삽입 순서도 기억합니다. 아무 값(객체, 원시 값)이나 키 또는 값으로 사용할 수 있습니다.

## Map 객체 사용하기

```javascript
var myMap = new Map();

var keyString = "어떤 문자열",
  keyObj = {},
  keyFunc = function() {};

// 값 저장하기
myMap.set(keyString, "'어떤 문자열'과 연결된 값");
myMap.set(keyObj, "keyObj와 연결된 값");
myMap.set(keyFunc, "keyFunc와 연결된 값");

myMap.size; // 3

// 값 불러오기
myMap.get(keyString); // "'어떤 문자열'과 연결된 값"
myMap.get(keyObj); // "keyObj와 연결된 값"
myMap.get(keyFunc); // "keyFunc와 연결된 값"

myMap.get("어떤 문자열"); // "'어떤 문자열'과 연결된 값"
// 왜냐면 keyString === '어떤 문자열'
myMap.get({}); // undefined, keyObj !== {}
myMap.get(function() {}); // undefined, keyFunc !== function () {}
```

> https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Map
