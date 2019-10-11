# useEffect

## 요약

### `useEffect`로 componentDidMount

`useEffect(fn, [])`로 가능 componentDidMount와 달리 prop과 state를 잡아둡니다. 그래서 콜백안에서도 prop과 state를 확인할 수 있습니다.

### `useEffect` 안에서 데이터 페칭은 어떻게 해야할까? 두번째 인자로 오는 배열([]) 은 뭐지?

### 이펙트를 일으키는 의존성 배열에 함수를 명시해도 되는걸까?

### 왜 가끔씩 데이터 페칭이 무한루프에 빠지는걸까?

> https://rinae.dev/posts/a-complete-guide-to-useeffect-ko?fbclid=IwAR1yTKQS1WXvGmuNEoLljb943CjiiVFxlCuf8LNWQry3_Iv6J1LZFFvvRFs
