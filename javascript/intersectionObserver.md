# 🎍intersectionObserver API

## 사용되는 경우들..

- 이미지 Lazy Loading
- Infinite scrolling, 비동기 무한 스크롤 UI
- 광고매출 측정을 위해 배너 또는 광고 노출여부
- 애니메이션 작업을 수행할 지 노출 여부를 사용하여 결정

이전에는 `.getBoundingClientRect()` 와 `window.innerHeight`으로 가시성에 정보를 얻음

## IntersectionObserver API 사용

```javascript
const io = new IntersectionObserver(callback, {
  root: null, // 또는 scrollable 한 element
  rootMargin: "0px", // 지정하지 않으면 기본값은 0px 입니다,
  threshold: 0.5 // 0.0 부터 1.0 사이의 숫자를 지정할 수 있습니다. 배열 값도 가능합니다
});
```

### root

root 의 값은 Element 또는 null 입니다
target (관측 대상) 을 감싸는 element 를 지정한다고 할 수 있습니다
만약 null 로 지정한다면 viewport 가 됩니다

문서 내의 scrollable 한 요소가 있고 `<div class="scroll"></div>`
관측 하고자 하는 element 가 그 안에 있다고 가정하면 `<img class="lazy-loaded-image">`
root 의 값은 `document.querySelector('.scroll')` 이 됩니다

### rootMargin

root 요소를 감싸는 margin 값을 지정합니다
문자열로 작성해야 하며, css의 margin 처럼 px 또는 % 단위로 작성할 수 있습니다
threshold 나 교차 상태를 점검할 때 margin 값이 지정 되어 있다면, 이를 활용하여 계산합니다

### threshold

target element 가 root 와 몇 % 교차했을 때, callback 을 실행할지 결정하는 값 입니다
값은 float 값으로 된 단일값 또는 배열값을 입력할 수 있고
0.0 부터 1.0 까지의 부동 소수점 값을 입력합니다

예를 들어, 스크롤 하는 중에 element 가 50% 보였을 때 실행할 callback 이 있다고 하면
threshold 값은 0.5 가 됩니다

또는, element 가 보이는 것을 여러 구간에서 callback 을 실행하고 싶다면
배열로 작성하면 됩니다

element 의 노출도 10% 당 무언가의 동작을 하고 싶다면, threshold 는
[0.0, 0.1, 0.2, 0.3, ..., 0.9, 1.0] 이 되겠죠!

### callback

callback 은 target element 의 visibility 가 threshold 만큼 도달했을 때 호출될 함수 입니다
Element 배열인 entries와 자기 자신인 observer 가 매개 변수로 전달 됩니다

```javascript
new IntersectionObserver(
  (entries: Element[], observer: IntersectionObserver) => {
    /* ... */
  },
  {}
);
```

entries 는 target 으로 지정한 DOM element 객체입니다.
보통은 callback 함수는 실제 역치 (threshold) 에 도달 했을 때 실행할 동작을 작성합니다!

## Example

### Lazy Loading

```html
<head>
  <style>
    div.image-box {
      display: block;
      margin: 20px auto 0;
      width: 200px;
      height: 200px;
      background-color: #acacac;
      color: #ffffff;
      text-align: center;
      line-height: 200px;
      font-size: 24px;
    }
  </style>
</head>
<body>
  <div class="image-box" data-src="https://source.unsplash.com/random/200x200">
    No Image
  </div>
</body>
```

```javascript
const images = document.querySelectorAll(".image-box");
const threshold = 0.8;
const lazyLoadOption = { root: null, threshold };
const lazyLoadImage = (entries, observer) => {
  entries.forEach(entry => {
    const { target } = entry;
    if (entry.isIntersecting) {
      target.style.backgroundImage = `url("${target.dataset.src}")`;
      target.style.backgroundSize = `cover`;
      target.style.backgroundColor = `transparent`;
      target.textContent = "";

      observer.unobserve(target);
    }
  });
};
const lazyLoadingIO = new IntersectionObserver(lazyLoadImage, lazyLoadOption);
images.forEach(image => lazyLoadingIO.observe(image));
```

### Infinite Scrolling

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0"
    />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Infinite Scrolling 🤞</title>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.css"
    />
    <style>
      * {
        box-sizing: border-box;
        list-style: none;
      }
      .title {
        font-size: 24px;
        font-family: "Tahoma", sans-serif;
        text-align: center;
        margin-top: 20px;
        font-weight: bold;
      }
      ul.infinite-container {
        display: block;
        width: 500px;
        margin: 0 auto;
      }
      li.cat {
        width: 300px;
        height: 300px;
        margin: 20px auto 0;
      }
      img {
        display: inline-block;
        width: 300px;
        height: 300px;
        object-fit: cover;
      }
    </style>
  </head>
  <body>
    <h1 class="title">Obey the cats 🐈</h1>
    <ul class="infinite-container"></ul>
    <script type="application/javascript">
      const container = document.querySelector("ul.infinite-container");
      const lastChild = () => document.querySelector("ul > li:last-child");
      let currentLast = null;

      const createNewCats = (numberOfCats = 10) => {
        const acc = [];
        const createNewCat = () => {
          const $li = document.createElement("li");
          $li.className = "cat";
          const $img = document.createElement("img");
          $li.appendChild($img);
          $img.src = `https://source.unsplash.com/featured/?cat?t=${Math.random()}`;
          $img.alt = "cat";
          return $li;
        };
        for (let i = 0; i < numberOfCats; i++) {
          acc.push(createNewCat());
        }
        return acc;
      };

      const loadingNewCats = newCats => {
        const loadingTemplate = `<li class="cat loading"><span>Loading New Cats...</span></li>`;
        return new Promise((resolve, reject) => {
          container.insertAdjacentHTML("beforeend", loadingTemplate);
          setTimeout(() => {
            resolve(newCats);
            container.removeChild(container.lastChild);
          }, 1000);
        });
      };

      const handleInfiniteScrolling = (entries, observer) => {
        const $last = [...entries].pop();
        if ($last.isIntersecting) {
          loadingNewCats(createNewCats()).then(newCats => {
            container.append(...newCats);
            currentLast = lastChild();
            observer.unobserve($last.target);
            observer.observe(currentLast);
          });
        }
      };

      const ioOptions = {
        root: null,
        threshold: 1
      };

      const io = new IntersectionObserver(handleInfiniteScrolling, ioOptions);
      container.append(...createNewCats());
      io.observe(lastChild());
    </script>
  </body>
</html>
```
