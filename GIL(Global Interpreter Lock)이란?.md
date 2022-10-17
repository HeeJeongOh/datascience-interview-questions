# GIL(Global Interpreter Lock)이란 무엇인가?

## 정의

- 파이썬 코드를 실행할 때 여러 `thread`를 사용한다면, 하나의 thread만이 객체에 접근할 수 있도록 제한하는 `mutex`이다. GIL이 필요한 이유는 메모리를 관리하는 방법이 `thread-safe`하지 않기 때문이다.
    - **Thread**: 프로세스 내부의 흐름
    - **mutex(Mutual Exclusion)**: 다중 Thread(프로세스) 환경에서 Critical section이 겹치지 않게 각각 단독으로 실행하게 하는 제약
    - **thread-safe**: 공유 자원에 대해 여러 thread가 동시에 접근했을 때, 갱신된 내용을 보장할 수 있는 상태 (참고 `Race Condition`)

## 배경

thread-safe를 보장하기 위해 파이썬에서는 GIL을 사용한다. 하지만 이로 인해 파이썬은 멀티쓰레딩이 오히려 싱글쓰레딩보다 느려질 수 있는 문제가 발생한다. 

3개의 thread를 사용해서 작업을 하는 경우를 가정해본다면, 상식적으로 3개의 thread가 동시에(simultaneous) 병렬적으로 처리할 것이라고 생각하기 쉽다. 하지만 실제로는 그렇지않고, 아주 짧은 시간동안 번갈아가면서 각 스레드가 조금씩 실행된다. 이를 구현하는 방법은 여러가지가 있고 파이썬은 그중에서 GIL을 사용한다. 

![https://user-images.githubusercontent.com/76675506/196156728-ecbfc40f-92f5-4837-98e3-4a956a9d6839.png](https://user-images.githubusercontent.com/76675506/196156728-ecbfc40f-92f5-4837-98e3-4a956a9d6839.png)

## 굳이 GIL을 사용하는 이유

- 파이썬은 기본적으로 `garbage collection`과 `reference counting`을 통해 메모리를 관리한다. 그런데 멀티스레드가 하나의 객체를 사용한다면 reference count의 일관성이 보장되지 않을 수 있는 문제가 발생할 수 있다. 이를 위해 mutex를 이용할 수 있는데, 각 thread 하나하나마다 mutex를 사용하는 것은 성능적으로도 좋지 않고, `deadlock`이라는 문제를 발생시킬 수도 있다.
    - **garbage collection**: 유효하지 않은 메모리를 정리해주는 시스템
    - **reference counting**: 객체가 참조될 때 증가하고 참조가 삭제되면 감소되는 방식으로 동작. counting이 0이 되면 삭제 대상이 된다.
    - **deadlock**: 두 개 이상의 작업이 서로 상대방의 작업이 끝나는 걸 기다리고만 있는 상태. 결국 둘 다 영원히 완료될 수 없다.
- 이를 해결하기 위해 파이썬에서는 mutex를 이용해 모든 Reference를 보호하지 않고 python interpreter를 잠궈버린다.

## 실제로 사용할 때

- 기본적으로 병렬 처리가 필요할 땐 numpy/scipy 등을 이용해 GIL 바깥에서 C 코드로 연산을 처리할 수 있다.
- 혹은 thread 대신 multiprocessng이나 asyncio 등을 통해 처리할 수 있다.