# 📍Interface

```typescript
interface SquareConfig {
  color?: string;
  width?: number;
}
function createSquare(config: SquareConfig): { color: string; area: number } {
  let newSquare = { color: "white", area: 100 };
  if (config.color) {
    newSquare.color = config.color;
  }
  if (config.width) {
    newSquare.area = config.width * config.width;
  }
  return newSquare;
}
let mySquare = createSquare({ color: "black" });
```

Optional propery를 가지는 인터페이스는 다른 인터페이스와 비슷하게 작성되며, 단지 프로퍼티 선언의 이름 끝에 ?가 추가 됩니다.

Optional propery의 장점은 인터페이스의 일부가 아닌 프로퍼티의 사용을 방지하고 사용 가능한 프로퍼티을 열거할 수 있다는 것입니다. 예를 들어 createSquare에서 color 프로퍼티의 이름을 잘못 입력했다면 다음과 같은 오류 메시지가 표시됩니다.

```typescript
interface SquareConfig {
  color?: string;
  width?: number;
}
function createSquare(config: SquareConfig): { color: string; area: number } {
  let newSquare = { color: "white", area: 100 };
  if (config.color) {
    // Error: Property 'clor' does not exist on type 'SquareConfig'
    newSquare.color = config.clor;
  }
  if (config.width) {
    newSquare.area = config.width * config.width;
  }
  return newSquare;
}
let mySquare = createSquare({ color: "black" });
```

## 읽기전용 프로퍼티

```typescript
interface Point {
  readonly x: number;
  readonly y: number;
}
```

### readonly vs const

readonly 와 const중에 어떤걸 사용할지 결정하는 가장 쉬운 방법은 변수 또는 프로퍼티 중 어떤 형태를 사용하느냐에 따라 결정합니다. 변수는 const를 사용하고 프로퍼티는 readonly를 사용합니다.
