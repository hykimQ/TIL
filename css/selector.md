# &#127749; Selector

## \* &#128656;

별도의 페이지에 있는 전체 요소를 대상으로 합니다.

```css
* {
  margin: 0;
  padding: 0;
}
```

자식 선택자에도 사용할 수 있습니다. 그래도 사용을 지양해야 합니다.

```css
#container * {
  border: 1px solid black;
}
```

## X Y (descendant) &#128692;

```css
li a {
  text-decoration: none;
}
```

가장 많이 언급하는 선택자는 descendant입니다. 선택자를 이용해 더 상세히 작업해야 할 때, 이 선택자를 사용합니다. 가령, 전체 앵커 태그를 대상으로 하기보다 순서를 매기지 않는 목록(unordered list)에 있는 앵커만 대상으로 한다면 어떨까요? 하위 선택자를 사용하면 상세해집니다.

> 선택자가 X Y Z A B.error처럼 보이면 여러분은 작업을 잘못하고 있습니다. 모든 요소에 꼭 가중치를 둬야 하는지를 늘 생각하세요.

## X > Y &#127745;

```css
div#container > ul {
  border: 1px solid black;
}
```

일반 X Y와 X > Y의 차이점은 후자가 직계 자식만을 선택한다는 것입니다.

```html
<div id="container">
  <ul>
    <li>
      List Item
      <ul>
        <li>Child</li>
      </ul>
    </li>
    <li>List Item</li>
    <li>List Item</li>
    <li>List Item</li>
  </ul>
</div>
```

#container > ul 선택자는 id가 container인 div의 직계 자손인 ul만 대상으로 삼습니다. 예를 들어 첫 번째 li의 자식인 ul은 대상이 되지 않습니다.

이런 이유로 자식 선택자를 이용해 성능을 향상할 수 있습니다. 사실, 자바스크립트를 기반으로 하는 CSS 선택자 엔진으로 작업할 때 추천합니다.

> https://code.tutsplus.com/ko/tutorials/the-30-css-selectors-you-must-memorize--net-16048
