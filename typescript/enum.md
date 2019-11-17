# Enum

## 사용법

```typescript
enum Color {
  RED,
  GREEN,
  BLUE
}

function setColor(color: Color) {
  // ...
}
setColor(Color.RED);
```

num은 하나의 타입이기도 하지만, JavaScript 런타임에서도 사용되는 하나의 변수로 볼 수도 있다. JavaScript 런타임에서도 사용된다는 말은, 클래스처럼 컴파일 결과물이 존재한다는 것이다. 예를 들어, 위에서 선언한 Color 타입은 아래와 같이 컴파일 된다.

```javascript
var Color;
(function(Color) {
  Color[(Color["RED"] = 0)] = "RED";
  Color[(Color["GREEN"] = 1)] = "GREEN";
  Color[(Color["BLUE"] = 2)] = "BLUE";
})(Color || (Color = {}));
```

enum 키워드는 기본적으로 리버스 매핑(reverse mapping)을 지원한다. 리버스 매핑이란 키로 값을 얻을 수 있을 뿐만 아니라, 값으로도 키를 얻을 수 있는 방식을 말한다. 그렇기 때문에 아래와 같은 형태로 객체가 생성된 것이다.

```javascript
var Color = {
  RED: 0,
  GREEN: 1,
  BLUE: 2,
  0: "RED",
  1: "GREEN",
  2: "BLUE"
};
```

## 선언과 값 초기화

enum으로 만들어진 변수에는 내부적으로 값이 할당된다. 별도의 명시가 없다면 값은 0부터 시작해서 1씩 증가하는 형태로 할당된다. C언어에서 보았던 Enum과 비슷한 형태다. 반대로, 별도의 명시를 해준다면 원하는 값으로 초기화 할 수 있다.

```typescript
enum Color {
  RED = 10,
  GREEN = 20,
  BLUE = RED + GREEN
}
```

Bitwise 연산자를 이용해서 일종의 플래그처럼 활용할 수도 있다. 하지만, 대개의 경우 숫자 값은 의미가 없으므로, DB에 값을 삽입할 때를 위해서 의미가 있는 문자열 값으로 초기화하고 싶은 경우도 있다. 그럴 때는 아래처럼 그냥 문자열 값을 선언해주면 된다.

```typescript
enum Color {
  RED = "red",
  GREEN = "green",
  BLUE = "blue"
}

// TypeScript 2.3 이하
enum Color {
  RED = <any>"red",
  GREEN = <any>"green",
  BLUE = <any>"blue"
}
```

두 가지 방법에는 큰 차이점이 있다. 바로 리버스 매핑의 유무. 2.4 버전 이상에서 문자열로 Enum 값을 초기화 하는 경우, 리버스 먜핑을 지원하지 않는다. 즉,

```typescript
console.log(Color[Color.RED]); // undefined
```

공식적인 이유는 찾지 못했는데, 아마 리버스 매핑을 지원한다면 Key와 Value가 충돌하는 문제를 회피하기 어려워서가 아닐까 한다. 2.3 버전에서는 리버스 매핑을 지원하는 것이 아니라, 어디까지나 문제를 우회해서 선언한 것이므로 충돌 문제는 개발자가 스스로 피해야 한다.

## const enum

enum 키워드는 앞에 const와 함께 사용할 수도 있다. const와 함께 사용할 경우, Enum은 컴파일 결과물을 가지지 않는다.

원래 enum으로 정의한 모든 변수들은 기본적으로 읽기 전용이지만, 간단한 트릭을 이용하면 런타임에서 쉽게 값을 변경할 수 있었다.

```typescript
(Color as any).RED = "yellow";
```

물론, 실제로 이렇게 위험한 코드를 짜는 경우는 거의 없겠지만. 아무튼 const enum을 사용한다면 이 문제를 근본적으로 회피할 수 있다. 애초에 런타임에 생기는 객체가 없기 때문에 수정할 대상 자체가 사라지는 것이다. 물론 이 경우에는 위 코드는 컴파일도 불가능하다. 이것이 첫 번째 차이점이다.

두 번째로, 리버스 매핑을 지원하지 않는다. 마찬가지로 리버스 매핑 문법 자체가 컴파일 에러가 난다. 애초에 리버스 매핑이 런타임에 존재하는 객체를 이용하는 것이므로 안되는 것이 당연한 것이지만.

세 번째로, 컴파일 타임에 평가할 수 없는 표현식으로 값을 할당할 수도 없게 된다. 이것을 간단히 예제로 설명하면,

```typescript
const green = 30;

const enum Color {
  RED = 10,
  BLUE = RED * 2,
  GREEN = green // ERROR: [ts] In 'const' enum declarations member initializer must be constant expression.
}
```

위 코드에서는 GREEN을 선언할 때 컴파일 에러가 난다. enum 키워드의 바깥에서 정의한 변수가 표현식으로 사용되면 컴파일 에러가 나는 것이다. 물론, RED처럼 enum 키워드 내부에서 선언한 변수들은 잘 평가된다. 이 특징도 어찌보면 당연한 건데, 컴파일 타임에 평가하지 못한 표현식은 런타임에 평가할 수 밖에 없고, 그렇게 되면 항상 같은 값임을 보장할 수가 없기 때문이다.

> https://www.typescriptlang.org/docs/handbook/enums.html > https://hyunseob.github.io/2017/07/18/typescript-enums/
