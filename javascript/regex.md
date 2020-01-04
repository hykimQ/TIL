# ➗정규식 (Regular expressions)

## 정규식

정규식 패턴이 지속적인 경우

```javascript
var re = /ab+c/;
```

정규식 패턴이 변경되는 경우

```javascript
var re = new RegExp("ab+c");
```

## 단순 문자열 패턴

```javascript
/abc/.exec("this is abc");

// result : ["abc"]

/abc/.exec("this is ab c");
// result : nul
```

## 정규식 사용

정규식은 ExgExp 메소드에 test, exec, String 메소드에 match, replace, search, split 메소드와 함께 사용됩니다.

- exec: 매칭된 문자열이 있다면 매칭된 값의 배열을 리턴하고, 매칭된 문자열이 없다면 null을 리턴합니다.

- test: 매칭된 문자열이 있다면 ture를 리턴하고, 매칭된 문자열이 없다면 false를 리턴합니다.

### example

```javascript
var myArray = /d(b+)d/g.exec("cdbbdbsbz");

var myRe = /d(b+)d/g; // 또는, var myRe = new RegExp('d(b+)d', 'g');
var myArray = myRe.exec("cdbbdbsbz");
```

- match: 매칭된 문자열이 있다면 매칭된 값의 배열을 리턴하고, 매칭된 문자열이 없다면 null을 리턴합니다.

- search: 매칭된 문자열이 있다면 매칭된 문자열의 인덱스를 리턴하고, 매칭된 문자열이 없다면 -1를 리턴합니다.

- replace: 매칭된 문자열을 찾아 매칭된 문자열을 변경하는 메소드입니다.

- split: 매칭된 문자열을 찾아 그 문자열을 기준으로 문자열을 나누는 메소드입니다.

### example

```javascript
var str = "abcde";
var myArray = str.match(/a(b)c(d)/);
console.log(myArray);

var re = /(\w+)\s(\w+)/;
var str = "John Smith";
var newstr = str.replace(re, "$2, $1");
console.log(newstr);
```

> https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D
