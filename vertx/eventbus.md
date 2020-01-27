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

pub/sub 메세징과 함께 여러분은 publishers로 부터 모든 메세지들을 받는다수의 subscriber를 갖을 수 있습니다.

receiver 는 들어오는 메세지들을 위해 이벤트 버스 상에 주소를 리스닝합니다.
메세지를 받았을 때, 로그를 남깁니다.

Sender는 메세지를 그 주소에 매초 마다 전달 하고, 그 응답을 받을 때 마다 로그를 남깁니다.

Java event bus pubsub receiver : https://github.com/vert-x3/vertx-examples/blob/master/core-examples/src/main/java/io/vertx/example/core/eventbus/pubsub/Receiver.java

```java
@Override
public void start() throws Exception {
    EventBus eb = vertx.eventBus();
    eb.consumer("news-feed", message -> System.out.println("Received news: " + message.body()));
    System.out.println("Ready!");
}
```

```java
@Override
public void start() throws Exception {
    EventBus eb = vertx.eventBus();
    // Send a message every second
    vertx.setPeriodic(1000, v -> eb.publish("news-feed", "Some news!"));
}

```

## MessageCodec

어떠한 객체 타입이든지 send / publish / receive 하기 위한 custom MessageCodec 을 작성하는 법을 설명합니다.
여러분은 String 과 같은 원시 타입 뿐만 아니라 EventBus를 통해 custom data type objects 를 직접 전달 할 수 있다라는 의미 입니다.

> https://kimseunghyun76.tistory.com/410
