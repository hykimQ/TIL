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

## Map의 키로 NaN 사용하기

NaN도 키로 사용할 수 있습니다. 모든 NaN은 자기 자신과 동일하지 않지만(NaN !== NaN), NaN을 구분할 수도 없기 때문에 아래 예제도 잘 동작합니다.

```javascript
var myMap = new Map();
myMap.set(NaN, "not a number");

myMap.get(NaN); // "not a number"

var otherNaN = Number("foo");
myMap.get(otherNaN); // "not a number"
```

## Array 객체와의 관계

```javascript
var kvArray = [["key1", "value1"], ["key2", "value2"]];

// 2D Array를 일반적인 Map constructor를 이용하여 Map 인스턴스를 만든다.
var myMap = new Map(kvArray);

myMap.get("key1"); // returns "value1"

// Spread 연사자를 이용하여 map을 2D key-value Array로 변환한다.
console.log(uneval([...myMap])); // Will show you exactly the same Array as kvArray

// 혹은 keys나 values iterator에 spread operator를 사용하여 키나 값들의 Array를 얻는다.
console.log(uneval([...myMap.keys()])); // Will show ["key1", "key2"]
```

> https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Map
