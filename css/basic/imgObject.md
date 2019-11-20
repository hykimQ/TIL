# CSS3 오브젝트 채우기, 위치조정 (object-fit, object-position) 속성

## object-fit

- 대체되는 요소의 내용(img, video, object,svg)이 지정된 너비와 높이에 맞게 장착되는 방식을 지정

- 프로필 이미지나 고정된 크기의 썸네일을 출력하는 다양한 경우처럼 제 각각의 크기를 가진 오브젝트등을 넘겨받아 비율을 유지한 채로 일정한 크기로 재가공하는 경우에 유용(background-size 속성과 유사)

## object-fit 속성 값

### object-fit: fill

- 대체되는 요소의 내용이 지정된 너비와 높이에 따라 크기가 확대(scale up) 혹은 축소(down), 늘어나거나(stretch) 움츠러든다(shrunk). 요소를 가득 채울수 있는 크기로 변화되면서 종횡비는 유지되지 않는다. 이것은 일반적으로 이미지에 강제로 너비와 높이를 지정하는 것과 같다.

### object-fit: contain

- 내용이 종횡비를 유지하면서 요소에 정의된 너비와 높이안에서 가능한한 많이 확대(scale up)시킨다

### object-fit: cover

- 내용이 종횡비를 유지하면서 정의된 너비와 높이를 가득 채울때까지 확대된다

### object-fit: none

- 내용의 크기가 요소의 크기와는 상관없이 기본 알고리즘에 의해 조정된다. 이 알고리즘은 원본의 크기에 가운데 정렬된 형태를 띈다

### object-fit: scale-down

- 내용의 크기를 아무것도 지정되지 않거나 혹은 contain 이 지정되어 있는 것처럼 변경한다. 이는 원본 크기보다 작아지는 결과를 보여준다.

## object-position

- object-fit 속성은 기본적으로 요소의 가운데로 화상을 이동시킨다. 이 위치를 원하는 값으로 변경하는 것이 object-position 속성이다.

- 기본 값은 50% 50%
- 숫자형 px, em, % 등이 사용되며, 키워드 top, left, right, bottom이 사용

> [WEBDIR](https://webdir.tistory.com/486)
