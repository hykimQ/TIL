# 🎢클로저

- 비공개 변수를 가질 수 있는 환경에 있는 함수

```javascript
var makeClosure = function() {
  var name = "zero";
  return function() {
    console.log(name);
  };
};
var closure = makeClosure(); // function () { console.log(name); }
closure(); // 'zero';
```

closure 함수 안에 console.log(name)이 있는데요. name은 closure 함수의 매개변수도 아니고, closure 함수 내부에서 생성한 변수도 아닙니다.
바로 이런 것이 비공개 변수
function() { console.log(name) }은 name 변수나, name 변수가 있는 스코프에 대해 클로저
수학적으로는 자유변수라

```javascript
"전역 컨텍스트": {
  변수객체: {
    arguments: null,
    variable: [{ makeClosure: Function }, 'closure'],
  },
  scopeChain: ['전역 변수객체'],
  this: window,
}
"makeClosure 컨텍스트": {
  변수객체: {
    arguments: null,
    variable: [{ name: 'zero' }],
  },
  scopeChain: ['makeClosure 변수객체', '전역 변수객체'],
  this: window,
}


//closure 호출 후
"closure 컨텍스트":  {
  변수객체: {
    arguments: null,
    variable: null,
  scopeChain: ['closure 변수객체', 'makeClosure 변수객체', '전역 변수객체'],
  this: window,
}
```

```javascript
var counter = function() {
  var count = 0;
  function changeCount(number) {
    count += number;
  }
  return {
    increase: function() {
      changeCount(1);
    },
    decrease: function() {
      changeCount(-1);
    },
    show: function() {
      alert(count);
    }
  };
};
var counterClosure = counter();
counterClosure.increase();
counterClosure.show(); // 1
counterClosure.decrease();
counterClosure.show(); // 0
```

counter 함수는 호출 시 return을 통해 counterClosure 컨텍스트에 비공개 변수인 count에 접근할 수 있는 scope chain을 반환합니다. 그렇게 되면 이제 counterClosure에서 계속 count로 접근할 수 있는 거죠. return 안에 들어 있는 함수들은 count 변수나, changeCount 함수 또는 그것들을 포함하고 있는 스코프에 대한 클로저라고 부를 수 있습니다.

단점으로는 잘못 사용했을 시 성능 문제와 메모리 문제가 발생

- ex) event

```javascript
// error 클릭 시 계산된 i 5을 참조함
for (var i = 0; i < 5; i++) {
  $("#target" + i).on("click", function() {
    alert(i);
  });
}

// IIFE를 사용하여 클로저를 만들어주면 j 값은 i에 해당하는 숫자로 고정
for (var i = 0; i < 5; i++) {
  (function(j) {
    $("#target" + j).on("click", function() {
      alert(j);
    });
  })(i);
}
```
