# 함수 표현식, 선언식

## 함수 선언식(Function Declarations)

```javascript
function funcDeclarations() {
  return "A function declaration";
}
funcDeclarations(); // 'A function declaration'
```

## 함수 표현식(Function Expressions)

```javascript
var funcExpression = function() {
  return "A function expression";
};
funcExpression(); // 'A function expression'
```

- 함수 선언식은 호이스팅에 영향 받음
- 함수 표현식은 호이스팅에 영향 받지 않음

```javascript
// 실행 전
logMessage();
sumNumbers();

function logMessage() {
  return "worked";
}

var sumNumbers = function() {
  return 10 + 20;
};
```

```javascript
// 실행 시
function logMessage() {
  return "worked";
}
var sumNumbers;

logMessage(); // 'worked'
sumNumbers(); // Uncaught TypeError: sumNumbers is not a function

sumNumbers = function() {
  return 10 + 20;
};
```

## 함수 표현식 장점

- 클로져로 사용

클로져를 사용하지 않은 예

```javascript
var tabs = document.querySelectorAll(".tab");
var i;

for (i = 0; i < tabs.length; i += 1) {
  tabs[i].onclick = function(event) {
    console.log(i); // 어느 탭을 클릭해도 항상 tabs.length (i 의 최종 값) 이 출력
  };
}
```

클로져 적용 후

```javascript
function tabsHandler(index) {
  return function tabClickEvent(event) {
    // 바깥 함수인 tabsHandler 의 index 인자를 여기서 접근할 수 있다.
    console.log(index); // 탭을 클릭할 때 마다 해당 탭의 index 값을 표시
  };
}

var tabs = document.querySelectorAll(".tab");
var i;

for (i = 0; i < tabs.length; i += 1) {
  tabs[i].onclick = tabsHandler(i);
}
```

- 콜백으로 사용(다른 함수의 인자로 넘김)
