# 📱미디어 쿼리

미디어 쿼리는 단말기의 유형(출력물 vs. 화면)과, 어떤 특성이나 수치(화면 해상도, 뷰포트 너비 등)에 따라 웹사이트나 앱의 스타일을 수정할 때 유용합니다.

## @media(at media)

```css
@media mediaqueries {
  /* style rules  */
}
```

@media 로 시작하며, 이 키워드는 이제부터 미디어 쿼리를 시작한다 라는 뜻입니다.

그 뒤에 미디어 쿼리 구문(위 코드의 mediaqueries) 이 나오고 이어서 중괄호( { } )를 이용해서 스타일 규칙이 들어갑니다.

미디어 쿼리 구문은 논리적으로 평가되며 참이면 뒤에 나오는 스타일 규칙이 적용되고, 거짓이면 무시됩니다.

미디어 쿼리 구문은 미디어 타입(Media Types)과 미디어 특성(Media Features)으로 이루어져 있습니다.

## Example

```css
@media all and (min-width:768px) {
    사용자 해상도가 768px 이상일 때 이 코드가 실행됨. 테블릿과 데스크톱의 공통 코드를 작성한다.
}

@media all and (min-width:768px) and (max-width:1024px) {
    사용자 해상도가 768px 이상이고 1024px 이하일 때 이 코드가 실행됨. 아이패드 또는 비교적 작은 해상도의 랩탑이나 데스크톱에 대응하는 코드를 작성한다.
}

@media all and (min-width:1025px) {
    사용자 해상도가 1025px 이상일 때 이 코드가 실행됨. 1025px 이상의 랩탑 또는 데스크톱에 대응하는 코드를 작성한다.
}
```

@media (max-width: 768px) {...} 처럼 미디어 타입을 생략하면 all 이 기본값이 되어 모든 미디어 타입에 적용

## 미디어 유형

- all: 모든 장치에 적합
  - all 타입은 모든 미디어에 적용되는 타입입니다. 미디어를 구분하는 용도가 아니기 때문에 유용하게 사용되지는 않습니다.
- print: 인쇄 결과물 및 출력 미리보기 화면에 표시 중인 문서
- screen: 주로 화면 대상
  - 화면을 출력하는 디스플레이가 있는 미디어들은 전부 screen에 속하기 때문에 현실적으로 고려해야하는 미디어들은 전부 여기에 해당이 됩니다.
- speech: 음성 합성장치 대상

## 미디어 특성

- width: width는 뷰포트의 너비, 즉 브라우저 창의 너비를 말합니다.

- orientation: orientation은 미디어가 세로모드인지 가로모드인지를 구분합니다.

  미디어 쿼리에서는 이 구분을 width와 height 특성의 값을 비교해서 height가 width보다 같거나 크면 세로모드

  반대인 경우에는 가로모드라고 해석합니다. 세로모드에서는 portrait, 가로모드에서는 landscape 키워드와 매칭이 됩니다.

## 논리 연산자

- and
- not
- only
- , (미디어 쿼리에 포함된 콤마구분 리스트는 or 연산자와 같은 동작)

## Etc

```css
@media all and (min-width: 568px) {
}

@media all and (min-width: 768px) {
}

@media all and (min-width: 1025px) {
}

/* min-width가 가장 작은 값이 적용됨 */
```

> [MDN CSS Media query](https://developer.mozilla.org/ko/docs/Web/Guide/CSS/Media_queries)
