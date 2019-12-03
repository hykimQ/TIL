# visibility

요소의 화면 표시 여부를 지정하는 속성입니다.

기본 값 : visible

```css
visibility: visible | hidden | collapse | initial | inherit;
```

## 속성

- visible

  화면에 표시

- hidden

  화면에 표시되지 않음(공간은 차지함)

- collapse

  셀 간의 경계를 무시하고 숨김(테이블 관련 요소에만 적용 가능)

```css
visibility: visible; /* 보임 기본값 */
visibility: hidden; /* 숨김, 자신의 박스 영역은 유지(margin까지 모두 포함) */
visibility: collapse; /* 셀간의 경계를 무시하고 숨김(박스영역 없음, 테이블의 행과 열 요소에만 지정 가능, 그 외 요소 지정은 hidden과 같음) */
```

## display: none과 차이점

- display: none: 요소가 렌더링 되지 않음(DOM에 존재하지 않음)
- visibility: hidden: 요소가 보이지는 않지만 렌더링 되며 화면에 공간을 가지고 있음(DOM에 존재함)
