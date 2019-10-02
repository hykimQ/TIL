# 미디어 쿼리

미디어 쿼리는 단말기의 유형(출력물 vs. 화면)과, 어떤 특성이나 수치(화면 해상도, 뷰포트 너비 등)에 따라 웹사이트나 앱의 스타일을 수정할 때 유용

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
- print: 인쇄 결과물 및 출력 미리보기 화면에 표시 중인 문서
- screen: 주로 화면 대상
- speech: 음성 합성장치 대상

## 미디어 특성

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
