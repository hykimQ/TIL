# Optional Chaning

## Example &#9997;

#### Conditional operator

```typescript
let username =
  data === null || data === undefined ? undefined : data.user.name();
```

#### Optional Chaining

```typescript
let x = data?.user.name();
```

## 반환값 &#9997;

`?.` 연산자는 좌측의 값에 대해 null인지 undefined인지 확인하고 해당한다면 이후 속성을 찾는 작업은 중지하고 undefined를 반환합니다.

## &&와 차이점 &#9997;

`?.`연산자는 기존 코드에서 많이 사용된 `&&`를 대체할 수 있겠지만 둘은 엄밀히 체크하는 타입이 다릅니다.
&&연산자는 앞의 피연산자가 falsy(false, null, undefined, '', 0, NaN)인지 확인하지만 `?.`연산자는 null과 undefined만을 확인합니다.

## Optional 요소에의 접근 &#9997;

```typescript
function getFirstElement<T>(arr: T[]) {
  return arr?.[0]
}
```

arr은 Optional이지만 간단하게 내부 요소에 접근하는 코드를 작성할 수 있습니다.

## Optional 함수 실행 &#9997;

```typescript
function makeLog(log?:(message: string) => void) {
  return log?.('log가 null이나 undefined가 아니라면 실행될 거예요!')
}
```
