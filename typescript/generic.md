# 🏷제너릭 함수

타입 변수를 이용해 위의 getFirstElem 함수를 다음과 같이 제너릭 함수로 정의할 수 있다.

```typescript
function getFirstElem<T>(arr: T[]): T {
  /* 함수 본문 */
}

임의의 타입 T에 대해, getFirstElem은 T 타입 값의 배열 arr를 인자로 받아 T 타입 값을 반환하는 함수다.
```

보다 일반적으로는 다음과 같은 꼴이 된다. 이 때 인자 타입과 반환 타입을 표현할 때 타입 변수를 사용할 수 있다.

```typescript
function 함수명<타입 변수>(인자 타입): 반환 타입 {
  /* 함수 본문 */
}
```

함수를 호출 할 때에는 정의에서 매개변수가 있던 자리에 인자를 넣어준다. 마찬가지로, 제너릭 함수를 호출할 때에는 정의에서 타입 변수가 있던 자리에 타입 인자를 넣어준다.

```typescript
const languages: string[] = ["TypeScript", "JavaScript"];
const language = getFirstElem<string>(languages); // 이 때 language의 타입은 문자열
```

## 제너릭 타입 별칭

타입 별칭 정의에도 제너릭을 사용할 수 있다. 이 때 타입 변수 정의는 별칭 이름 다음에 붙여 쓴다.

```typescript
type MyArray<T> = T[];
const drinks: MyArray<string> = ["Coffee", "Milk", "Beer"];
```

## 제너릭의 사용처

타입 변수와 제너릭의 핵심은 여러 타입에 대해 동작하는 요소를 정의하되, 해당 요소를 사용할 때가 되어야 알 수 있는 타입 정보를 정의에 사용하는 것이다. 이러한 개념이 적용되는 범위는 함수와 타입 별칭에 국한되지 않는다. 제너릭을 이용해 추후 다룰 인터페이스, 클래스 등 다양한 타입의 표현력을 높힐 수 있다.
