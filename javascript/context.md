# 실행 컨텍스트

```javascript
var name = "zero"; // (1)변수 선언 (6)변수 대입
function wow(word) {
  // (2)변수 선언 (3)변수 대입
  console.log(word + " " + name); // (11)
}
function say() {
  // (4)변수 선언 (5)변수 대입
  var name = "nero"; // (8)
  console.log(name); // (9)
  wow("hello"); // (10)
}
say(); // (7)
```

- 처음 코드를 실행(브라우저가 스크립트를 로드해서 실행)하는 순간 전역 컨텍스트 생성
- 함수를 호출할 때 함수 컨텍스트 생성

## 컨텍스트 원칙

1. 먼저 전역 컨텍스트 생성 후, 함수 호출 시마다 함수 컨텍스트 생성
2. 컨텍스트 생성 시 안에 변수객체(argument, variable), scope chain, this가 생성
3. 컨텍스트 생성 후 함수가 실행되는데 사용되는 변수들은 안에서 찾고 없으면 scope chain을 따라 올라가며 찾음
4. 함수 실행이 끝나면 해당 컨텍스트는 사라짐, 페이지가 종료되면 전역 컨텍스트가 사라짐

## 전역 컨텍스트

this는 따로 설정하지 않으면 window, this를 바꾸는 방법은 new를 호출 또는 함구에 다른 this값을 bind

```javascript
'전역 컨텍스트': {
  변수객체: {
    arguments: null,
    variable: ['name', 'wow', 'say'],
  },
  scopeChain: ['전역 변수객체'],
  this: window,
}
```

이제 코드를 위에서 부터 실행, wow와 say는 호이스팅에 의해 선언과 동시에 대입됨

## 함수 컨텍스트

```javascript
'say 컨텍스트': {
  변수객체: {
    arguments: null,
    variable: ['name'], // 초기화 후 [{ name: 'nero' }]가 됨
  },
  scopeChain: ['say 변수객체', '전역 변수객체'],
  this: window,
}
```

wow호출 후 wow함수 컨텍스트 생성

```javascript
'wow 컨텍스트': {
  변수객체: {
    arguments: [{ word : 'hello' }],
    variable: null,
  },
  scopeChain: ['wow 변수객체', '전역 변수객체'],
  this: window,
}
```

wow 사용하는 변수를 variable에서 찾는데 없으면 scope chain을 따라 올라감(함수 선언 시점에 lexical scope)

wow 종료 후 wow컨텍스트는 사라지고 그 후에 say도 종료하면 say컨텍스트도 사라짐, 마지막으로 전역 컨텍스트가 사라짐
