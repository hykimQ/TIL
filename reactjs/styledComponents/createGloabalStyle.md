# Create Global Styles

```javascript
import { createGlobalStyle } from "styled-components";

const GlobalStyle = createGlobalStyle`
  body {
    margin: 0;
    padding: 0;
    background: teal;
    font-family: Open-Sans, Helvetica, Sans-Serif;
  }
`;

export default GlobalStyle;
```

```javascript
import React, { Fragment } from "react";
import GlobalStyle from "./theme/globalStyle";
import Content from "./components/Content";

function App() {
  return (
    <Fragment>
      <GlobalStyle />
      <Content />
    </Fragment>
  );
}

export default App;
```
