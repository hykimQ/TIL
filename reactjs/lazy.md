# 🔌React.lazy

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

## Error boundaries

네트워크 장애로 인하여 다른 모듈이 로드에 실패한 경우 오류가 발생할 수 있다. 이런 경우 Error Boundaries를 이용하여 사용자 환경을 개선 및 복구 관리할 수 있다. Error Boundary를 만들어 lazy 컴포넌트를 감싸 네트워크 오류가 발생할때 오류 상태를 표시할 수 있다.

```javascript
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // Update state so the next render will show the fallback UI.
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    // You can also log the error to an error reporting service
    logErrorToMyService(error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      // You can render any custom fallback UI
      return <h1>Something went wrong.</h1>;
    }

    return this.props.children;
  }
}
```

```javascript
import MyErrorBoundary from "./MyErrorBoundary";
const OtherComponent = React.lazy(() => import("./OtherComponent"));
const AnotherComponent = React.lazy(() => import("./AnotherComponent"));

const MyComponent = () => (
  <div>
    <MyErrorBoundary>
      <Suspense fallback={<div>Loading...</div>}>
        <section>
          <OtherComponent />
          <AnotherComponent />
        </section>
      </Suspense>
    </MyErrorBoundary>
  </div>
);
```

## Route-based code spliting(라우터기반 코드 스플릿팅)

어플리케이션에서 code splitting을 적용할 위치를 결정하는 것은 까다로울 수 있습니다. 사용자 경험에 지장을 주지않고 번들을 균등하게 분할할 영역을 선택해야 합니다.

적용하기 좋은 곳은 route입니다. 웹페이지 로드 시간은 대부분 페이지 전환에 발생하며, 페이지를 한번에 렌더링하는 것이 대부분이므로 렌더링 중간에 사용자가 페이지와 상호 작용할 가능성은 거의 없습니다.

다음은 React Router와 같은 라이브러리를 사용한 어플리케이션에 React.lazy를 사용하여 경로 기반 code splitting하는 예제입니다.

```javascript
import { BrowserRouter as Router, Route, Switch } from "react-router-dom";
import React, { Suspense, lazy } from "react";

const Home = lazy(() => import("./routes/Home"));
const About = lazy(() => import("./routes/About"));

const App = () => (
  <Router>
    <Suspense fallback={<div>Loading...</div>}>
      <Switch>
        <Route exact path="/" component={Home} />
        <Route path="/about" component={About} />
      </Switch>
    </Suspense>
  </Router>
);
```

## Named Exports

React,lazy는 현재 export default만 지원합니다. 만약 named export를 사용한 경우 default로 이름을 재정의 하는 중간 모듈을 생성 할 수 있습니다. 아래와 같이 한다면 treeshaking이 계속 작동하고 사용하지 않는 컴포넌트를 가져오지 않게 됩니다.

```javascript
// ManyComponents.js
export const MyComponent = /* ... */;
export const MyUnusedComponent = /* ... */;

// MyComponent.js
export { MyComponent as default } from "./ManyComponents.js";

// MyApp.js
import React, { lazy } from 'react';
const MyComponent = lazy(() => import("./MyComponent.js"));
```

> https://velog.io/@odini/Code-Splitting%EC%BD%94%EB%93%9C-%EC%8A%A4%ED%94%8C%EB%A6%BF%ED%8C%85

> https://reactjs.org/docs/code-splitting.html
