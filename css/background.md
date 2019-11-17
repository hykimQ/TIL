# background

## background 관련 속성

### background-color

기본 값 : transparent

배경의 색상을 지정하는 속성입니다.

### background-image

기본 값 : none

배경으로 사용할 이미지의 경로를 지정하는 속성입니다.
url의 경로는 절대 경로, 상대 경로 모두 사용 가능합니다.
만약 background-color에 색상이 적용된 상태에서 background-image로 사용된 이미지에 투명한 부분이 있다면,
그 부분에 background-color 색상이 노출됩니다.

### background- repeat

기본 값 : repeat

이미지의 반복 여부와 방향을 지정하는 속성입니다.
기본값이 repeat이기 때문에 따로 설정하지 않으면 x, y축으로 반복되어서 표시됩니다.
background-repeat의 값으로 사용할 수 있는 것들은 다음과 같습니다.

- repeat

  x, y축 으로 모두 반복합니다.

- repeat-x

  x 축 방향으로만 반복합니다.

- repeat-y

  y 축 방향으로만 반복합니다.

- no-repeat

  이미지를 반복하지 않습니다.

### background-position

기본 값 : 0% 0%

요소에서 배경 이미지의 위치를 지정하는 속성입니다. x축, y축으로부터의 위치를 지정할 수 있으며, 값의 선언 순서는 x축, y축으로부터의 간격입니다. 만일 한쪽만 지정된다면 나머지는 중앙 값(center)으로 적용됩니다.

- %

  기준으로부터 % 만큼 떨어진 지점과 이미지의 % 지점이 일치하는 곳에 위치시킵니다.

- px

  기준으로부터 px 만큼 떨어진 지점과 이미지의 (0,0) 지점이 일치하는 곳에 위치시킵니다.

키워드

top, left, right, bottom, center 키워드를 사용할 수 있습니다.

키워드는 선언 순서와 관계없이 top, bottom은 y축 기준으로 하며 left, right는 x축을 기준으로 합니다.

### background-attachment

기본 값 : scroll

화면 스크롤에 따른 배경 이미지의 움직임 여부를 지정하는 속성입니다.

- scroll

  배경 이미지는 요소 자체를 기준으로 고정되어 있으며 내용과 함께 스크롤 되지 않습니다.

- local

  배경 이미지는 요소의 내용을 기준으로 고정되어 있으며 내용과 함께 스크롤 됩니다.

- fixed

  배경 이미지는 뷰포트를 기준으로 고정되어 있으며 스크롤에 영향을 받지 않습니다.

> 뷰포트 : 사용자가 시각적으로 볼 수 있는 웹페이지 영역을 의미합니다. 컴퓨터나 휴대폰과 같은 장치에 Display 요소가 표현되는 영역을 말합니다.

### background 축약

```css
background: [-color] [-image] [-repeat] [-attachment] [-position];
```

## Example

```html
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <title>background</title>
    <style>
      div {
        height: 500px;
        background-color: yellow;
        background-image: url(https://www.w3schools.com/CSSref/img_tree.gif);
        background-repeat: no-repeat;
        background-position: center top;
        /* 축약형 */
        background: yellow url(https://www.w3schools.com/CSSref/img_tree.gif)
          no-repeat center top;
      }
    </style>
  </head>
  <body>
    <div>css background 속성 실습</div>
  </body>
</html>
```

> https://www.w3schools.com/cssref/css3_pr_background-size.asp > https://www.edwith.org/boostcourse-ui/lecture/33521/
