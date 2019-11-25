# 🎐font

지켜야 할 규칙이 많고 가독성이 좋지 않기 때문에

실무에서 선호하는 편은 아닙니다.

그렇지만 font로 선언된 속성을 보고 어떤 값들이 적용되어 있는지 해석할 수 있어야 합니다.

## font 관련 속성

font-style, font-variant, font-weight, font-size/line-height, font-family 속성들을 한 번에 선언할 수 있는 축약형 속성입니다.

```css
font: font-style font-variant font-weight font-size/line-height font-family |
  initial | inherit;
```

- font-style

  font-style 지정, 기본 값은 normal

- font-variant

  font-variant 지정, 기본 값은 normal

- font-weight

  font-weight 지정, 기본 값은 normal

- font-size/line-height

  font-size/line-height 지정, 기본 값은 normal

- font-family

  font-family 지정

```css
/* style | size | family */
font: oblique 2em "돋움", dotum, sans-serif;

/* style | variant | weight | size/line-height | family */
font: oblique small-caps bold 16px/1.5 "돋움";

/* The font used in system dialogs */
font: message-box;
font: icon;
```

- font-size와 font-family는 반드시 선언해야 하는 필수 속성입니다.
- 빠진 속성이 있다면 기본 값으로 지정됩니다.
- 각 속성의 선언 순서를 지켜야 합니다.
