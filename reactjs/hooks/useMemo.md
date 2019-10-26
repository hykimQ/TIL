# useMemo

```javascript
import React, { useEffect, useState } from "react";

const User = () => {
  const [nickname, setNickname] = useState("");
  const [nicknameLength, setNicknameLength] = useState(0);

  const updateNicknameLength = () => {
    setNicknameLength(nickname.length);
  };
  useEffect(updateNicknameLength, [nickname]);

  const updateNickname = event => {
    const nickname = event.target.value;

    setNickname(nickname);
  };

  return (
    <div>
      <input onChange={updateNickname} />
      <label>{nicknameLength}</label>
    </div>
  );
};
```

```javascript
import React, { useMemo, useState } from "react";

const User = () => {
  const [nickname, setNickname] = useState("");
  const nicknameLength = useMemo(() => nickname.length, [nickname]);

  const updateNickname = event => {
    const nickname = event.target.value;

    setNickname(nickname);
  };

  return (
    <div>
      <input onChange={updateNickname} />
      <label>{nicknameLength}</label>
    </div>
  );
};
```

> https://ko.reactjs.org/docs/hooks-reference.html#usememo > https://rinae.dev/posts/review-when-to-usememo-and-usecallback
