# 🕳Immutable js

1. 객체는 Map
2. 배열은 List
3. 설정할 땐 set
4. 읽을 땐 get
5. 읽은 다음에 설정할 땐 update
6. 내부에 있는걸 ~할 땐 In을 붙인다(setIn, getIn, updateIn)
7. 일반 자바스크립트 객체로 변환할 땐 toJS()
8. List엔 배열 내장함수와 비슷한 함수들이 있음 (push, slice, filter, sort, concat, ...) : 전부 불변함을 유지함
9. 특정 key를 지울 땐(혹은 List에서 원소를 지울 때)delete

```javascript
import React from "react";
import { render } from "react-dom";
import App from "./App";
import { Map, List } from "immutable";

// 1. 객체는 Map
const obj = Map({
  foo: 1,
  inner: Map({
    bar: 10
  })
});

console.log(obj.toJS());

// 2. 배열은 List
const arr = List([Map({ foo: 1 }), Map({ bar: 2 })]);

console.log(arr.toJS());

// 3. 설정할땐 set
let nextObj = obj.set("foo", 5);
console.log(nextObj.toJS());
console.log(nextObj !== obj); // true

// 4. 값을 읽을땐 get
console.log(obj.get("foo"));
console.log(arr.get(0)); // List 에는 index 를 설정하여 읽음

// 5. 읽은다음에 설정 할 때는 update
// 두번째 파라미터로는 updater 함수가 들어감
nextObj = nextObj.update("foo", value => value + 1);
console.log(nextObj.toJS());

// 6. 내부에 있는걸 ~ 할땐 In 을 붙인다
nextObj = obj.setIn(["inner", "bar"], 20);
console.log(nextObj.getIn(["inner", "bar"]));

let nextArr = arr.setIn([0, "foo"], 10);
console.log(nextArr.getIn([0, "foo"]));

// 8. List 내장함수는 배열이랑 비슷하다
nextArr = arr.push(Map({ qaz: 3 }));
console.log(nextArr.toJS());
nextArr = arr.filter(item => item.get("foo") === 1);
console.log(nextArr.toJS());

// 9. delete 로 key 를 지울 수 있음
nextObj = nextObj.delete("foo");
console.log(nextObj.toJS());

nextArr = nextArr.delete(0);
console.log(nextArr.toJS());

render(<App />, document.getElementById("root"));
```
