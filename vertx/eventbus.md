# Event Bus

## Point to Point

receiver와 sender 사이에 point to point 메세징

- receiver는 들어오는 메세지들을 위한 이벤트 버스 상의 주소에 리스닝(메세지를 받을 때 메세지에 응답)
- sender는 매 초 그 주소상에 메세지를 보냄, 응답을 받을 때 그것에 대한 로그를 찍음

```java
// receiver

@Override
public void start() throws Exception {
    EventBus eb = vertx.eventBus();
    eb.consumer("ping-address", message -> {
        System.out.println("Received message: " + message.body());
        // Now send back reply
        message.reply("pong!");
    });
    System.out.println("Receiver ready!");
}
```

```java
// sender

@Override
public void start() throws Exception {
    EventBus eb = vertx.eventBus();
    // Send a message every second
    vertx.setPeriodic(1000, v -> {
        eb.send("ping-address", "ping!", reply -> {
            if (reply.succeeded()) {
                System.out.println("Received reply " + reply.result().body());
            } else {
                System.out.println("No reply");
            }
        });
    });
}
```

## Publish / Subscibe

## MessageCodec

> https://kimseunghyun76.tistory.com/410
