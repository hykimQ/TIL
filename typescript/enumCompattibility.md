# 🎟열거형의 호환성

열거형의 호환성은 객체 타입이 연관된 경우에 비해 상당히 간단하다. 다른 열거형으로부터 유래된 값끼리는 호환되지 않는다.

```typescript
enum Status {
  Ready,
  Waiting
}
enum Color {
  Red,
  Blue,
  Green
}
let status: Status = Status.Ready;
status = Color.Green; // error
```

숫자 열거형 값은 number에, 문자열 열거형 값은 string에 할당 가능하다.

```typescript
enum MyEnum {
  Zero,
  One = 1,
  Name = "안희종"
}
const zero: number = MyEnum.Zero;
const one: number = MyEnum.One;
const name: string = MyEnum.Name;
```
