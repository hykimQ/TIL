# 도메인 여러개 설정

server 블럭을 추가해준다.

```
server {
  listen 80;
  server_name webisfree.com
  root /var/www/webisfree.com/
  index index.html index.htm
  ...
}

server {
  listen 80;
  server_name abcde.com
  root /var/www/abcde.com
  index index.html index.htm
  ...
}
```
