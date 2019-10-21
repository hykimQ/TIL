# video

`<video>`요소는 비디오를 삽입하는 표준적인 방법을 제공한다.

- width, height속성은 항상 함께 사용하는 것이 좋다. 설정하지 않으면 비디오에 대한 공간을 남겨둘 수 있어서비디오가 로딩될 동안 페이지 구성이 바뀔 수 있다.

- video요소를 지원하지 않는 브라우저를 위해 대체내용도 같이 넣는다.

```html
<video controls width="250">
  <source src="/media/examples/flower.webm" type="video/webm" />

  <source src="/media/examples/flower.mp4" type="video/mp4" />

  Sorry, your browser doesn't support embedded videos.
</video>
```

`<source>`요소를 이용해 여러개의 비디오 소스를 표시할 수 있고 브라우저가 가장 적절한 것을 선택한다.

## 속성

### height

비디오의 화면 높이(px)

### width

비디오의 화면 너비(px)

### autoplay

이 속성을 지정하면 비디오가 로드되고 자동으로 재생한다.

```html
<video autoplay>
  <video autoplay="autoplay"></video>
</video>
```

### controls

재생에 관한 조절 장치를 보여준다.

```html
<video controls>
  <video controls="controls"></video>
</video>
```

### loop

비디오를 반복 재생한다.

```html
<video loop>
  <video loop="loop"></video>
</video>
```

### muted

비디오에 포함된 오디오의 음소거를 결정한다.(default false)

```html
<video muted>
  <video muted="muted"></video>
</video>
```

### preload

비디오 파일을 로드하는 방법을 지정한다.

- **_none_**: 비디오 파일을 로드하지 않는다.
- **_metadata_**: metadata만 로드한다.
- **_auto_**: 전체 비디오 파일을 로드한다.

설정하지 않으면 브라우저의 기본 속성값을 지정한다.(명세에서는 metadata 설정을 권고)

```html
<video preload="none|metadata|auto"></video>
```

autoplay를 지정하면 preload는 무시한다.

### poster

비디오가 다운되어 있거나 사용자가 재생버튼을 누를 때까지 보이는 이미지 url을 지정한다.

### src

삽입할 비디오의 주소를 지정한다.

## 지원하는 파일 형식

- **_MP4_**: IE, Chrome, FF, Safari
- **_WebM_**: Chrome, FF, Opera
- **_ogg_**: Chrome, FF, Opera

> https://developer.mozilla.org/ko/docs/Web/HTML/Element/Video
