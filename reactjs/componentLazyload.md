# Component Lazy Loading

## Component Lazy Loading(Code Splitting)

```javascript
import React, { Suspense, lazy } from "react";

const LazyComponent = lazy(() => import("./LazyComponent"));

function Component() {
  return (
    <Suspense fallback={null}>
      <LazyComponent />
    </Suspense>
  );
}

export default Component;
```

## Component Preloading

### Ex) 컴포넌트 Preload 타이밍

1. 버튼 클릭에 컴포넌트가 필요한 경우 버튼 MouseEnter

2. 최초 페이지가 로드되고 모든 컴포넌트의 마운트가 끝났을 때

```javascript
import React, { Suspense, lazy, useEffect } from "react";

function lazyWithPreloading(importFunction) {
  const Component = React.lazy(importFunction);
  Component.preload = importFunction;
  return Component;
}

const LazyComponent = lazyWithPreloading(() => import("./LazyComponent"));

function Component() {
  // 2. 최초 페이지가 로드되고 모든 컴포넌트의 마운트가 끝났을 때
  useEffect(() => {
    LazyComponent.preload();
  }, []);

  // 1. 버튼 클릭에 컴포넌트가 필요한 경우 버튼 MouseEnter
  const handleMouseEnter = () => {
    LazyComponent.preload();
  };

  return (
    <div>
      <button onMouseEnter={handleMouseEnter}>Click!</button>
      <Suspense fallback={null}>
        <LazyComponent />
      </Suspense>
    </div>
  );
}

export default Component;
```
