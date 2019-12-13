# Union Types

때로는 파라미터가 number 또는 string이 될 것으로 기대하는 라이브러리를 실행하게 될때도 있습니다.

```typescript
/**
 * 문자열을 가져 와서 왼쪽에 'padding'을 추가합니다.
 * 'padding'이 문자열이면 'padding'이 왼쪽에 추가됩니다.
 * 'padding'이 숫자 인 경우 해당 개수의 공백이 왼쪽에 추가됩니다.
 */
function padLeft(value: string, padding: any) {
  if (typeof padding === "number") {
    return Array(padding + 1).join(" ") + value;
  }
  if (typeof padding === "string") {
    return padding + value;
  }
  throw new Error(`Expected string or number, got '${padding}'.`);
}
padLeft("Hello world", 4); // returns "    Hello world"
```

padLeft의 문제점은 padding 파라미터가 any로 입력된다는 것입니다. 즉, number나 string이 아닌 파라미터를 사용하여 호출할 수 있지만 TypeScript는 해당 파라미터를 수용합니다.

any 대신에 padding 파라미터에 Union 타입을 사용할 수 있습니다.

```typescript
/**
 * 문자열을 가져 와서 왼쪽에 "패딩"을 추가합니다.
 * 'padding'이 문자열이면 'padding'이 왼쪽에 추가됩니다.
 * 'padding'이 숫자 인 경우 해당 개수의 공백이 왼쪽에 추가됩니다.
 */
function padLeft(value: string, padding: string | number) {
  // ...
}
let indentedString = padLeft("Hello world", true); // errors during compilation
```

Union 타입은 여러 타입 중 하나 일 수 있는 값을 나타냅니다. 수직 막대 (|)를 사용하여 각 타입을 구분하므로 number | string | boolean은 number,string 또는boolean 일 수있는 값의 타입입니다.

만일 우리가 Union 타입을 가진 값을 가지고 있다면, Union의 모든 타입에 공통적인 멤버들만 접근할 수 있습니다.

```typescript
interface Bird {
  fly();
  layEggs();
}
interface Fish {
  swim();
  layEggs();
}
function getSmallPet(): Fish | Bird {
  // ...
}
let pet = getSmallPet();
pet.layEggs(); // okay
pet.swim(); // errors
```

Union 타입은 약간 까다로울 수 있지만 익숙해지기 위해서는 약간의 직감이 필요합니다. 타입이 A|B인 값을 가지고 있다면, 우리는 A와 B 둘 다 특정 멤버가 있음을 확실히 알 수 있습니다. 이 예제에서 Bird에는 fly라는 멤버가 있습니다. 그리고 Bird | Fish 타입에는 fly 메서드가 있음을 확신할 수 없습니다. 그렇기 때문에 런타임에 변수가 실제로 Fish 인 경우 pet.fly()를 호출하면 실패할 수 있습니다.
