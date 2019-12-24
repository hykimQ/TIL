# 🎊String replace

`replace()` 메서드는 어떤 패턴이 일치하는 일부 또는 모든 부분이 교체된 새로운 문자열을 반환한다. 그 패턴은 정규식, 문자열이 될 수 있다.

```javascript
var p =
  "The quick brown fox jumps over the lazy dog. If the dog reacted, was it really lazy?";

var regex = /dog/gi;

console.log(p.replace(regex, "ferret"));
// expected output: "The quick brown fox jumps over the lazy ferret. If the ferret reacted, was it really lazy?"

console.log(p.replace("dog", "monkey"));
// expected output: "The quick brown fox jumps over the lazy monkey. If the dog reacted, was it really lazy?"
```

## 매개변수

### 구문

```javascript
var newStr = str.replace(regexp|substr, newSubstr|function)
```

### `regexp` (pattern)

정규식(RegExp) 객체 또는 리터럴. 일치하는 항목은 newSubStr 또는 지정된 함수(function)가 반환 한 값으로 대체됩니다.

### `substr` (pattern)

newSubStr로 대체 될 String. 정규식이 아닌 글자 그대로의 문자열로 처리됩니다. 오직 첫 번째 일치되는 문자열만이 교체됩니다.

### `newSubStr` (replacement)

첫번째 파라미터를 대신할 문자열(String). 여러가지 대체 패턴들이 지원됩니다. 아래의 "매개변수가 string으로 지정되었을 때" 섹션을 참고하세요.

### `function` (replacement)

주어진 regexp 또는 substr에 일치하는 요소를 대체하는 데 사용될 새 하위 문자열을 생성하기 위해 호출되는 함수. 이 함수에 제공되는 인수는 아래 "매개변수가 function으로 지정되었을 때"단원에서 설명합니다.

## 매개변수가 string으로 지정되었을 때

replacement 문자열은 다음과 같은 특수 교체 패턴을 포함할 수 있습니다.

- \$$:	 "$" 기호를 삽입합니다.
- \$&: 매치된 문자열을 삽입합니다.
- \$`: 매치된 문자열 앞쪽까지의 문자열을 삽입합니다.
- \$': 매치된 문자열의 문자열을 삽입합니다.
- \$n:
  n이 1이상 99이하의 정수라면, 첫번째 매개변수로 넘겨진 RegExp객체에서 소괄호로 묶인 n번째의 부분 표현식으로 매치된 문자열을 삽입합니다.

### 문자열 단어 치환

```javascript
var re = /(\w+)\s(\w+)/;
var str = "John Smith";
var newstr = str.replace(re, "$2, $1");
console.log(newstr); // Smith, John
```

## 매개변수가 function으로 지정되었을 때

### match

매치된 문자열. (윗쪽의 \$& 표현식으로 매치된 경우와 동일합니다.)

### p1, p2,...

윗쪽의 $n 표현식과 동일합니다. ($1은 p1, \$2는 p2...) 예를 들어, 만약 정규표현식 /(\a+)(\b+)/ 이 주어진다면 p1은 \a+와 매치되고 p2는 \b+와 매치됩니다.

### offset

조사된 전체 문자열 중에서 매치된 문자열의 index.(예를 들어, 조사될 전체 문자열이 abcd이고, 매치된 문자열이 bc면 이 매개변수의 값은 1이 됩니다.)

### string

조사된 전체 문자열 (replace를 호출한 string)

```javascript
function f2c(x) {
  function convert(str, p1, offset, s) {
    return ((p1 - 32) * 5) / 9 + "C";
  }
  var s = String(x);
  var test = /(-?\d+(?:\.\d*)?)F\b/g;
  return s.replace(test, convert);
}
```

> https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/replace
