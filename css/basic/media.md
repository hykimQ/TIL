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

예제 코드

위에서 정의한 Syntax 따라 유효한 미디어 쿼리 예제 코드를 살펴보고 어떻게 해석이 되는지 같이 봅니다.

@media screen { ... }

미디어 타입이 screen이면 적용됩니다.

@media screen and (min-width: 768px) { ... }

미디어 타입이 screen이고 width가 768px 이상이면 적용됩니다. 두 개 중 하나라도 만족하지 않으면 거짓이 됩니다.

@media (min-width: 768px) and (max-width: 1024px) { ... }

and는 연결된 모든 표현식이 참이면 적용됩니다.(and 키워드는 연결된 부분이 모두 참이어야 적용이 됩니다.)

@media (color-index)

미디어 장치가 color-index를 지원하면 적용됩니다.

@media screen and (min-width: 768px), screen and (orientation: portrait), ...

쉼표로 연결된 미디어 쿼리 중 하나라도 참이면 적용됩니다.( and 키워드와 반대라고 생각하면 됩니다.)

@media not screen and (min-width: 768px)

not 키워드는 하나의 media_query 전체를 부정합니다.
(not screen) and (min-width: 768px) 잘못된 해석!
not (screen and (min-width: 768px)) 올바른 해석!
@media not screen and (min-width: 768px), print
첫 번째 미디어 쿼리에만 not 키워드가 적용되며, 두 번째 미디어 쿼리(print)에는 영향이 없습니다.

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

## Syntax

```css
media_query_list: S * [media_query [ "," S * media_query ] * ]?;
media_query: [ONLY | NOT]? S * media_type S * [ AND S * expression ] * |
  expression [ AND S * expression ] *;
expression: "(" S * media_feature S * [ ":" S * expr ]? ")" S *;
```

- media_query_list
  : 여러개의 미디어 쿼리로 이루어진 리스트로 작성 가능하며, 쉼표를 이용해서 구분합니다.

- media_query

  : A 형태 - 미디어 타입에 and 키워드를 이용해서 미디어 표현식을 붙일 수 있습니다.
  미디어 타잎 앞에는 only 또는 not 키워드가 올 수 있습니다.
  미디어 표현식은 생략 가능하기 때문에 미디어 타입 단독으로 사용될 수 있습니다.

  : B 형태 - 미디어 타입 없이 미디어 표현식이 바로 나올 수 있습니다.(미디어 타입이 명시되지 않으면 all로 간주합니다.)
  미디어 표현식은 and 키워드를 이용해서 계속해서 나올 수 있습니다.

- expression
  : 미디어 표현식은 괄호로 감싸야 하며, 특성 이름과 해당하는 값으로 이루어집니다. 이름과 값은 : 기호로 연결합니다.
  또, 값이 없이 특성 이름만으로도 작성할 수 있다.

Syntax는 전부 이해할 필요는 없지만 일부 기호는 알아두면 좋습니다.

- [ a ] : a가 나올 수도 있고 나오지 않을 수도 있습니다.
- a | b : a 또는 b 둘 중에 하나를 선택합니다.
  "|"는 파이프 라인 기호로 키보드의 역슬래시(\) 키를 Shift 키를 누른 채로 누르면 나옵니다.
- a? : a가 0번 나오거나 1번만 나올 수 있음
- a\* : a가 0번 나오거나 그 이상 계속 나올 수 있음
- media_type : all, screen, print 등 명세에 정의된 미디어 타입
- media_feature : width, orientation 등 명세에 정의된 미디어 특성

### min-/max- 접두사

미디어 특성은 이름 앞에 min- 또는 max- 접두사를 붙일 수 있습니다.

실제로 반응형 사이트를 제작할 때는 보통 접두사를 붙여서 사용합니다.

접두사를 붙이지 않고 사용하는 경우 대부분 효율적이지 못하기 때문입니다.

예를 들어 대부분의 반응형 사이트는 width 특성을 이용하는데, 접두사 없이 width: 00px 이라고 하게 선언하면

정확히 뷰포트의 크기가 00px 에서만 적용되기 때문에, 다양한 기기들을 대응하기 힘듭니다.

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
