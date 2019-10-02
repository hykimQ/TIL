# array 중복 제거

```javascript
const array = ["a", 1, 2, "a", "a", 3];

// 1: 'Set'
[...new Set(array)];

// 2: 'Filter'
array.filter((item, index) => array.indexOf(item) === index);

// 3: 'Reduce'
array.reduce(
  (unique, item) => (unique.includes(item) ? unique : [...unique, item]),
  []
);

// RESULT:
// ['a', 1, 2, 3]
```
