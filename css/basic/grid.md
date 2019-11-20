# Grid Layout

```html
<div class="wrapper">
  <div class="one">One</div>
  <div class="two">Two</div>
  <div class="three">Three</div>
  <div class="four">Four</div>
  <div class="five">Five</div>
  <div class="six">Six</div>
</div>
```

```css
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 10px;
  grid-auto-rows: minmax(100px, auto);
}
.one {
  grid-column: 1 / 3;
  grid-row: 1;
}
.two {
  grid-column: 2 / 4;
  grid-row: 1 / 3;
}
.three {
  grid-column: 1;
  grid-row: 2 / 5;
}
.four {
  grid-column: 3;
  grid-row: 3;
}
.five {
  grid-column: 2;
  grid-row: 4;
}
.six {
  grid-column: 3;
  grid-row: 4;
}
```

## fr

- fr은 유연한 크기를 갖는 단위
- 그리드 내의 공간 비율을 분수로 나타냄

```css
.grid {
  display: grid;
  grid-template-columns: auto 100px 1fr 2fr;
}
```

1. 1번 열은 auto를 사용: 해당 Element 내부 콘텐츠에 맞게 사이즈가 조정
2. 2번 열은 100px 할당: 100픽셀 크기만큼 폭 차지
3. 3번 열은 1fr 크기 할당: 1fr은 남은 자유 공간의 1/3(총fr)만큼 크기 할당
4. 4번 열은 2fr 크기 할당: 2fr은 남은 자유 공간의 2/3(총fr)만큼 크기 할당

```css
.grid {
  grid-template-columns: 100px 100px;
}
```
