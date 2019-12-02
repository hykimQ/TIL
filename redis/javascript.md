# Redis, Javascript

## install

```shell
npm i redis
```

```javascript
const redis = require("redis");
const client = redis.createClient();
```

## string

```javascript
client.set("name", "name!");
client.get("name", (err, reply) => {
  console.log(reply); // name!
});
```

## Publish / Subscribe

```javascript
var redis = require("redis");
var sub = redis.createClient(),
  pub = redis.createClient();
var msg_count = 0;

sub.on("subscribe", function(channel, count) {
  pub.publish("a nice channel", "I am sending a message.");
  pub.publish("a nice channel", "I am sending a second message.");
  pub.publish("a nice channel", "I am sending my last message.");
});

sub.on("message", function(channel, message) {
  console.log("sub channel " + channel + ": " + message);
  msg_count += 1;
  if (msg_count === 3) {
    sub.unsubscribe();
    sub.quit();
    pub.quit();
  }
});

sub.subscribe("a nice channel");
```
