# Pub/Sub

## 메시지 보내기, 받기

일반적인 데이터베이스와는 다르게 레디스는 메시지를 주고, 받는 기능을 제공합니다. Publish 명령으로 보내고, Subscribe 명령으로 받습니다.
통로는 채널(channel)을 이용합니다. 채널은 "SET KEY VALUE"에서 사용하는 'KEY'와 같은 것으로 생각하면 됩니다.
방법은 클라이언트1에서 subscribe channel_name를 실행하고, 클라이언트2에서 publish channel_name "Message"를 실행하면, 클라이언트1에 "Message"가 나옵니다.
레디스의 Pub/Sub 시스템은 메시지를 보관(queuing) 하지 않습니다. Publish 하는 시점에 이미 실행한 subscribe 명령으로 대기하고 있는 클라이언트들에게만 전달됩니다.

> http://redisgate.kr/redis/command/pubsub_intro.php
