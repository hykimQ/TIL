# React.memo()

## props 동등 비교 커스터마이징 (shouldComponentUpdate)

React.memo()는 props 혹은 props의 객체를 비교할 때 얕은(shallow) 비교를 한다.

비교 방식을 수정하고 싶다면 React.memo() 두 번째 매개변수로 비교함수를 만들어 넘겨주면 된다.

```javascript
React.memo(Component, [areEqual(prevProps, nextProps)]);
```

```javascript
function moviePropsAreEqual(prevMovie, nextMovie) {
  return (
    prevMovie.title === nextMovie.title &&
    prevMovie.releaseDate === nextMovie.releaseDate
  );
}

const MemoizedMovie2 = React.memo(Movie, moviePropsAreEqual);
```

> https://ui.toast.com/weekly-pick/ko_20190731/
