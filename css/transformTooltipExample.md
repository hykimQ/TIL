# 🎉Scale을 활용한 Tooltip

## Example

## `visibility`, `opacity`를 이용해 툴팁을 숨긴다.

```css
transform: translate(-50%, 0) scale(0);
opacity: 0;
visibility: none;
transition: all 0.2s ease-out;
transform-origin: 50% 100%;
```

`transform-origin`으로 transition 되는 시작점을 지정한다.

## `visibility`, `opacity` 값으로 툴팁을 보여준다.

```css
transform: translate(-50%, 0) scale(1);
visibility: visible;
opacity: 1;
```
