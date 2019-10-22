# React.lazy

`React.lazy`함수를 사용하면 dynamic import를 사용하여 가져온 컴포넌트를 렌더링 할 수 있다.

> `React.lazy`, `Suspense`는 아직 서버사이드 랜더링에 사용할 수 없다. 서버사이드 랜더링된 애플리케이션에서 code splitting기능을 사용하고 싶으면 [Lodable Components](https://github.com/smooth-code/loadable-components)를 추천한다.

### Before

```javascript
import OtherComponent from "./OtherComponent";

function MyComponent() {
  return (
    <div>
      <OtherComponent />
    </div>
  );
}
```

### After

```javascript
const OtherComponent = React.lazy(() => import("./OtherComponent"));

function MyComponent() {
  return (
    <div>
      <OtherComponent />
    </div>
  );
}
```

MyComponent 컴포넌트가 랜더링되면 OtherComponent컴포넌트를 포함한 번들이 자동으로 로드된다.

React 컴포넌트를 `export default`로 해석되는 Promise로 반환하고 `React.lazy`로 dynamic import()를 할때에는 함수 형태로 사용한다.

## Suspense

`Suspense` 컴포넌트를 사용한다면, MyComponent가 랜더링 될 때까지 동적으로 불러온 OtherComponent가 아직 로드가 되지 않은경우 로딩중과 같은 fallback content 표현이 가능하다.

```javascript
const OtherComponent = React.lazy(() => import("./OtherComponent"));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
```

fallback 기능은 컴포넌트가 로드 될 때까지 기다리는 동안 랜더링하려는 모든 React요소에 적용가능하다. `Suspense` 컴포넌트는 lazy 컴포넌트를 감쌉니다. 하나의 `Suspense` 컴포넌트로 여러 lazy 컴포넌트를 래핑할 수도 있다.

```javascript
const OtherComponent = React.lazy(() => import("./OtherComponent"));
const AnotherComponent = React.lazy(() => import("./AnotherComponent"));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <section>
          <OtherComponent />
          <AnotherComponent />
        </section>
      </Suspense>
    </div>
  );
}
```
