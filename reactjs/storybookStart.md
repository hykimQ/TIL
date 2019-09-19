# Stroy Book

[Storybook](https://storybook.js.org/)은 컴포넌트 단위의 개발 환경을 지원하는 도구이다.
개발자가 뷰를 개발 할 때 고립된 환경을 제공하여 관심사를 의존성과 환경으로부터 분리시켜주어 개발자가 뷰에 집중하여 스스로를 표현하는 컴포넌트 개발할 수 있게 한다.

## Installation

1. create-react-app을 통해 프로젝트 스캐폴딩

```console
$ create-react-app storybook-playground
```

2. storybook 설치(storybook은 고유의 커맨드라인 인터페이스를 갖춤, cli 설치)

```console
npm install -g @storybook/cli
```

3. 프로젝트에서 storybook 설치

```console
$ getstorybook
```

4. storybook 실행(package.json에 storybook관련 명령어 추가됨)

```console
$ npm run storybook
```

## Story 작성

프로젝트에 stories 폴더가 생기고 그안에 index.js파일에 storybook 예제가 있음

```javascript
import React from "react";

import { storiesOf } from "@storybook/react";
import { action } from "@storybook/addon-actions";
import { linkTo } from "@storybook/addon-links";

import { Button, Welcome } from "@storybook/react/demo";

storiesOf("Welcome", module).add("to Storybook", () => (
  <Welcome showApp={linkTo("Button")} />
));

storiesOf("Button", module)
  .add("with text", () => (
    <Button onClick={action("clicked")}>Hello Button</Button>
  ))
  .add("with some emoji", () => (
    <Button onClick={action("clicked")}>😀 😎 👍 💯</Button>
  ));
```

## Action 작성하기

- action은 Storybook에서 사용하는 일종의 로깅용 함수
- action은 이런 네이티브 이벤트 뿐만이 아니라 프로그래머가 직접 짠 이벤트에도 반응하도록 만들 수 있음
- action 자체는 함수를 반환하는 함수이므로 이벤트에 바인딩해도 로그를 남기지 않는다. 항상 문자열과 함께 함수를 실행시킨 결과를 이벤트에 바인딩

```javascript
storiesOf("Input", module)
  .add("default", () => <Input onChange={action("changed")} />)
  .add("disabled", () => <Input disabled />);
```

## 데코레이터(Decorator) 추가하기

래핑 컴포넌틑를 만들어 전체적인 뷰를 보기 편하게 할 수 있음

```javascript
import { storiesOf, addDecorator } from "@storybook/react";

// ...

storiesOf("Input", module)
  .addDecorator(story => <div style={{ margin: "50px" }}>{story()}</div>)
  .add("default", () => <Input onChange={action("changed")} />)
  .add("disabled", () => <Input disabled />);
```

addDecorator는 스토리 사이에도 껴넣을 수 있는데, 그러면 addDecorator의 뒤에 있는 스토리들만 그 데코레이터의 영향을 받는다.

## [애드온 설치하기](https://storybook.js.org/docs/addons/addon-gallery/): Background

storybook에 배경색을 바꿀 수 있는 애드온

```console
$ npm install @storybook/addon-backgrounds --dev
```

storybook 애드온은 .storybook/addon.js에 등록해줘야 함

```javascript
import "@storybook/addon-actions/register";
import "@storybook/addon-links/register";
import "@storybook/addon-backgrounds/register";
```

background 데코레이터 추가

```javascript
// ...

import backgrounds from "@storybook/addon-backgrounds";

// ...

storiesOf("Input", module)
  .addDecorator(story => <div style={{ margin: "50px" }}>{story()}</div>)
  .addDecorator(
    backgrounds([
      { name: "white", value: "#ffffff", default: true },
      { name: "pink", value: "#ff00ff" },
      { name: "black", value: "#000000" }
    ])
  )
  .add("default", () => <Input onChange={action("changed")} />)
  .add("disabled", () => <Input disabled />);
```

모든 컴포넌트에 이 배경화면 데코레이터를 적용하고 싶다면, .storybook/config.js 파일을 수정할 수도 있다.

```javascript
import { configure, addDecorator } from "@storybook/react";
import backgrounds from "@storybook/addon-backgrounds";

addDecorator(
  backgrounds([
    { name: "white", value: "#ffffff", default: true },
    { name: "pink", value: "#ff00ff" },
    { name: "black", value: "#000000" }
  ])
);

function loadStories() {
  require("../src/stories");
}

configure(loadStories, module);
```

## Story 파일 로드 설정

.storybook/config.js 파일에 loadStories파일 수정

```javascript
// ...

const req = require.context("../src/components", true, /\.stories\.(js|jsx)$/);

function loadStories() {
  req.keys().forEach(filename => {
    req(filename);
  });
}
```

require.context는 webpack에서 지원하는 함수다. Storybook은 내부적으로 webpack을 사용하기 때문에 쓸 수 있다. 이렇게 하면 src/components 아래에 있는 폴더란 폴더는 다돌면서 \*.stories.js 파일을 찾아 모두 로드시킨다.

## TypeScript 설정

.storybook/webpack.config.js 파일을 만들어서 아래와 같이 써주면 된다.

```javascript
const path = require("path");
const genDefaultConfig = require("@storybook/react/dist/server/config/defaults/webpack.config.js");

module.exports = (baseConfig, env) => {
  const config = genDefaultConfig(baseConfig, env);

  config.module.rules.push({
    test: /\.(ts|tsx)$/,
    include: path.resolve(__dirname, "../src"),
    loader: require.resolve("ts-loader")
  });
  config.resolve.extensions.push(".ts", ".tsx");

  return config;
};
```
