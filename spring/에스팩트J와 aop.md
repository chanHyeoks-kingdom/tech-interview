```
[ AspectJ의 AOP ]
Spring AOP 외에 또 다른 강력한 AOP 프레임워크 중 하나인 AspectJ는 프록시를 이용하지 않았다. 대신 AspectJ는 CGlib이라는 바이트 조작 라이브러리를 사용하여 타깃 오브젝트의 바이트를 고쳐서 부가기능을 직접 넣어주는 방법(바이트 조작)을 사용한다. 그래서 우리가 만든 코드에서는 부가 기능이 분리되어 있지만 바이트 코드에서는 핵심 기능과 부가 기능이 섞여있는 구조이다. AspectJ가 프록시를 사용하지 않고 CGLib을 이용한 복잡한 바이트 조작 방법을 사용하는 이유는 크게 2가지가 잇다.

바이트 코드를 조작하면 Spring과 같은 컨테이너의 도움이 필요 없기 때문이다.
프록시 방식보다 훨씬 강력하고 유연한 AOP를 제공할 수 있다.
 

프록시를 이용해 프록시를 구현하면 Spring의 빈으로 등록해야 하기 때문에 Spring에 종속적인 기술이 되어버린다는 단점이 있다. 반면에 바이트코드를 조작하면 스프링과 같은 컨테이너가 없는 환경에서도 AOP를 이용할 수 있다.

또한 바이트 조작으로 AOP를 구현하면 객체의 생성, 필드 값의 조회와 조작 등과 같은 다양한 부가 기능을 추가할 수 있다. 하지만 프록시를 이용하는 방법으로는 이러한 부가 기능을 처리하기가 어렵다.

 

그래도 대부분의 경우라면 Spring에서 제공하는 AOP로도 처리할 수 있다. 하지만 특별한 요구사항이 생겨서 Spring의 AOP로 처리가 어렵다면 AspectJ를 이용하면 된다.

```

https://mangkyu.tistory.com/161
