# 🎠fetch

```javascript
fetch("http://hanur.me/users")
  .then(res => res.json())
  .then(data => data.filter(item => item.isRequired));
```

## Header

```javascript
const reqHeader = new Headers();
const content = "HI";
reqHeader.append("Content-Type", "application/json");
reqHeader.append("Content-Length", content.length.toString());
```

```javascript
const content = "HI";
const reqHeader = new Headers({
  "Content-Type": "application/json",
  "Content-Length": content.length.toString()
});
```

## Request

```javascript
const req = new Request("/api/posts", {
  method: "GET",
  headers: new Headers({
    "content-type": "application/json"
  }),
  body: {
    name: "LeeHanur"
  }
});
```

```javascript
const req = new Request("/api/posts", {
  method: "GET",
  headers: new Headers({
    "content-type": "application/json"
  }),
  body: {
    name: "LeeHanur"
  }
});
// is not Fetched
fetch(req)
  .then(res => res.json())
  .then(data => console.log(data));
// is fetched Data!
```

## Response

- status
- statusText
- ok
- headers
- type
