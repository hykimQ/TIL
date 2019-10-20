# Semantic tag

## article

- article 요소는 내용이 독립적이고, 홀로 설 수 있는 내용을 담는다.
- 주로 블로그 포스트, 뉴스 기사 등을 article로 묵을 수 있다.

```html
<article>
  <h1>블로그</h1>
  <p>블로그 포스트</p>
</article>
```

## section

- section은 서로 관계 있는 문서를 분리하는 역할을 한다.
- 주로 문서를 다른 주제로 구분짓기 위해 사용한다.

```html
<section>
  <h1>블로그</h1>
  <p>블로그 포스트</p>
</section>
```

> ### article, section, div
>
> 1. 내용을 독립적이고 스스로 설 수 있는 내용은 article을 사용한다.
> 2. 내용이 서로 관계가 있다면 section을 사용한다.
> 3. 의미적으로 관계가 없다면 div를 사용한다.
>
> ---
>
> article은 스스로 설 수 있는 내용이라는 점에서 section보다 좀 더 구체적인 의미를 갖는다.
> 여러개의 section을 article로 묵을 수 있고 마찬가지로 여러개의 article을 section으로 묵을 수 있다.
