# vert.x

- vert.x는 Node.js에 영향을 받은 프로젝트
- vert.x는 Node.js처럼 Event-based 프로그래밍 모델을 제공하는 서버 프레임워크
- Node.js, vert.x 둘 모두 비동기 형태의 API제공

## vert.x의 설계 철학

- **Polyglot - 여러 언어 지원**

  vertx는 Java로 작성되었지만 Javascript, Ruby, Python 등 여러 언어를 지원한다.

- **Super Simple Concurrency model**

  vert.x로 서버 애플리케이션을 작성할 때, 사용자는 싱글 스레드 애플리케이션을 작성하듯 코드를 작성해도 괜찮다. vert.x는 사용자가 작성한 코드가 동일한 스레드에서만 실행됨을 보장해서 더 이상 synchronized나 volatile 같은 동기화를 위한 locking 처리를 신경 쓰지 않아도 된다. Node.js에서는 JavaScript 실행 엔진 자체가 멀티 스레드를 지원하지 않으므로 모든 CPU 코어를 활용하려면 같은 JavaScript 프로그램을 여러 개 실행해야 했다. 하지만 vert.x에서는 하나의 프로세스만 가동해도 CPU 코어 개수에 맞춰 멀티 스레드가 생성될 수 있다. 멀티 스레드와 관련된 작업은 vert.x가 하고, 사용자는 비즈니스 로직 구현에 집중할 수 있게 한 것이다.

- **Event Bus 제공**

  도입 부분에서 설명했듯이 vert.x의 목표는 '하나의 서버 프로세스 데몬'을 만드는 것에 그치지 않는다. vert.x로 만든 여러 서버 프로그램이 서로 원활하게 통신하게 하는 것까지도 목표에 두고 있다. 이를 위해 vert.x는 Event Bus를 제공한다. Point to Point나 Pub/Sub 같은 MQ 기능을 사용할 수 있다(Event Bus 기능을 제공하기 위해 vert.x는 Hazelcast라는 IMDG를 사용한다). 이런 Event Bus가 있기 때문에 서로 다른 언어로 작성된 서버 애플리케이션이 용이하게 통신할 수 있다.

- **Module System & Public Module Repository**

  vert.x에는 모듈 시스템이라는 것이 있다. 모듈 시스템은 일종의 컴포넌트로 이해할 수 있다. vert.x로 만든 서버 애플리케이션 프로젝트 자체를 모듈화한 것이다. 이런 방식으로 재사용성을 도모한다. 이렇게 만들어진 모듈은 Public Module Repository에 등록할 수 있다. Public Module Repository를 통해 모듈을 공유할 수 있는 것이다.

## Netty와 vert.x의 관계

vert.x는 다중 I/O처리에 Netty를 사용한다.
vert.x는 Netty와는 다른 독자적인 API와 기능을 제공하는 다른 목적의 서버 프레임워크다. Netty는 로우레벨 수준의 I/O를 다룰 수 있는 프레임워크고, vert.x는 그보다는 하이레벨 영역을 다룬다.

> https://d2.naver.com/helloworld/163784
