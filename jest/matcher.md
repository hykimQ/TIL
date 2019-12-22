# 🎎Matcher

## Common Matchers

```javascript
test("two plus two is four", () => {
  expect(2 + 2).toBe(4);
});
```

`expect(2 + 2)`는 "expectation" 오브젝트를 리턴한다. 일반적으로 matcher를 호출하는 것을 제외하고는 이런 expectation 오브젝트는 많지 않다.

`toBe`는 정확한 동등(객체 동등)을 테스트하기 위해 `Object.is`를 사용한다. 오브젝트 값을 체크하기 원한다면 `toEqual`을 사용한다.

```javascript
test("object assignment", () => {
  const data = { one: 1 };
  data["two"] = 2;
  expect(data).toEqual({ one: 1, two: 2 });
});
```

`toEqual`은 오브젝트 또는 배열의 모든 필드 값을 재귀적으로 체크한다.

## Truthiness

- `toBeNull` matches only null
- `toBeUndefined` matches only undefined
- `toBeDefined` is the opposite of toBeUndefined
- `toBeTruthy` matches anything that an if statement treats as true
- `toBeFalsy` matches anything that an if statement treats as false

```javascript
test("null", () => {
  const n = null;
  expect(n).toBeNull();
  expect(n).toBeDefined();
  expect(n).not.toBeUndefined();
  expect(n).not.toBeTruthy();
  expect(n).toBeFalsy();
});

test("zero", () => {
  const z = 0;
  expect(z).not.toBeNull();
  expect(z).toBeDefined();
  expect(z).not.toBeUndefined();
  expect(z).not.toBeTruthy();
  expect(z).toBeFalsy();
});
```

## Numbers

숫자를 비교하는 동등 matcher

```javascript
test("two plus two", () => {
  const value = 2 + 2;
  expect(value).toBeGreaterThan(3);
  expect(value).toBeGreaterThanOrEqual(3.5);
  expect(value).toBeLessThan(5);
  expect(value).toBeLessThanOrEqual(4.5);

  // toBe and toEqual are equivalent for numbers
  expect(value).toBe(4);
  expect(value).toEqual(4);
});
```

소수점 동일을 위해, 작은 반올림 에러를 일으키는 테스트를 원하지 않기 때문에, toEqual대신 toBeCloseTo 를 사용한다.

```javascript
test("adding floating point numbers", () => {
  const value = 0.1 + 0.2;
  //expect(value).toBe(0.3);           This won't work because of rounding error
  expect(value).toBeCloseTo(0.3); // This works.
});
```

## String

`toMatch`를 사용하여 정규식에 대해 문자열을 확인 할 수 있다.

```javascript
test("there is no I in team", () => {
  expect("team").not.toMatch(/I/);
});

test('but there is a "stop" in Christoph', () => {
  expect("Christoph").toMatch(/stop/);
});
```

## Arrays

`oContain`를 사용하여 배열에 특별한 item이 포함되어 있는지 확인 할 수 있다.

```javascript
const shoppingList = [
  "diapers",
  "kleenex",
  "trash bags",
  "paper towels",
  "beer"
];

test("the shopping list has beer on it", () => {
  expect(shoppingList).toContain("beer");
});
```

## Exceptions

특정 함수가 호출될 때 에러를 던진다는 것을 테스트하려면 `toThrow`를 사용한다.

```javascript
function compileAndroidCode() {
  throw new ConfigError("you are using the wrong JDK");
}

test("compiling android goes as expected", () => {
  expect(compileAndroidCode).toThrow();
  expect(compileAndroidCode).toThrow(ConfigError);

  // You can also use the exact error message or a regexp
  expect(compileAndroidCode).toThrow("you are using the wrong JDK");
  expect(compileAndroidCode).toThrow(/JDK/);
});
```
