# Transform

CSS3에서는 transform 속성을 사용하여 HTML 요소의 모양, 크기, 위치 등을 자유롭게 바꿀 수 있습니다.

transform 속성은 HTML 요소에 대해 다음과 같은 동작을 제공합니다.

- 해당 요소를 움직입니다.

- 해당 요소를 회전시킵니다.

- 해당 요소의 크기를 변경합니다.

- 해당 요소를 기울입니다.

- 해당 요소에 위의 네 가지 동작 중 원하는 동작들을 한 번에 적용시킵니다.

CSS3에서는 transform 속성을 사용하여 2D 변형(transform)과 3D 변형(transform)을 모두 제공합니다.

> http://tcpschool.com/css/css3_transform_2Dtransform

## 2D 변형(transform)

2D 변형(transform)을 위해 제공되는 메소드(method)는 다음과 같습니다.

### translate() 메소드

translate() 메소드는 현재 위치에서 해당 요소를 주어진 x축과 y축의 거리만큼 이동시킵니다.

주어진 거리가 양수이면 해당 축의 양의 방향으로, 음수이면 해당 축의 음의 방향으로 이동시킵니다.

```css
#trans {
  -webkit-transform: translate(100px, 50px);

  -ms-transform: translate(100px, 50px);

  transform: translate(100px, 50px);
}
```

### rotate() 메소드

rotate() 메소드는 해당 요소를 주어진 각도만큼 시계 방향이나 반시계 방향으로 회전시킵니다.

주어진 각도가 양수이면 시계 방향으로, 음수이면 반시계 방향으로 회전시킵니다.

```css
#rotate {
  -webkit-transform: rotate(30deg);

  -ms-transform: rotate(30deg);

  transform: rotate(30deg);
}
```

### scale() 메소드

scale() 메소드는 해당 요소의 크기를 주어진 배율만큼 늘리거나 줄입니다.

주어진 배율이 1보다 크면 크기를 늘리고, 0보다 크고 1보다 작으면 크기를 줄입니다.

```css
#scale_inc {
  -webkit-transform: scale(1.5, 2);

  -ms-transform: scale(1.5, 2);

  transform: scale(1.5, 2);
}

#scale_dec {
  -webkit-transform: scale(0.7, 0.7);

  -ms-transform: scale(0.7, 0.7);

  transform: scale(0.7, 0.7);
}
```

### skewX() 메소드

skewX() 메소드는 해당 요소를 주어진 각도만큼 x축 방향으로 기울입니다.

주어진 각도가 양수이면 x축의 양의 방향으로, 음수이면 x축의 음의 방향으로 기울입니다.

```css
#skew_x {
  -webkit-transform: skewX(20deg);

  -ms-transform: skewX(20deg);

  transform: skewX(20deg);
}
```

### skewY() 메소드

skewY() 메소드는 해당 요소를 주어진 각도만큼 y축 방향으로 기울입니다.

주어진 각도가 양수이면 y축의 양의 방향으로, 음수이면 y축의 음의 방향으로 기울입니다.

```css
#skew_y {
  -webkit-transform: skewY(20deg);

  -ms-transform: skewY(20deg);

  transform: skewY(20deg);
}
```

### skew() 메소드

skew() 메소드는 해당 요소를 주어진 각도만큼 각각 x축과 y축 방향으로 기울입니다.

```css
#skew {
  -webkit-transform: skew(20deg, 30deg);

  -ms-transform: skew(20deg, 30deg);

  transform: skew(20deg, 30deg);
}
```

### matrix() 메소드

matrix() 메소드는 모든 2D transform 메소드를 한 줄에 설정할 수 있도록 해줍니다.

이 메소드는 2D 변형(transform)과 관련된 6개의 매개변수를 가집니다.

matrix() 메소드의 매개변수 순서는 다음과 같습니다.

`matrix(scaleX(), skewY(), skewX(), scaleY(), translateX(), translateY());`

```css
#matrix {
  -webkit-transform: matrix(0.7, 0, 0, 0.7, 1, 0);

  -ms-transform: matrix(0.7, 0, 0, 0.7, 0, 0);

  transform: matrix(2, 0.3, 0.2, 1.3, 150, 100);
}
```
