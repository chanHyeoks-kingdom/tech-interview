## DI(Dependency Injection)가 뭐에요?

### 답변
        
        결합도를 낮추기 위해 "의존성을 외부에서 주입"받을 수 있는데 이를 "의존성 주입(DI)"라고 합니다.
        무슨 의미냐면 클래스 A에서 특정 객체 B가 필요할 때 클래스 A의 내부에서 객체 B를 생성하면 안된다는 의미입니다. 
        
        실제 예시로는, 스프링에서는 DI Container를 이용해 의존성 주입을 관리해 주는데, 별도의 Container를 사용하는 이유는
        SOLID 원칙의 SRP, OCP, DIP를 편리하게 준수하기 위해서입니다.



## 추가 질문: DI Container가 왜 필요한가요?
        
        별도의 DI 컨테이너가 없는 경우, 개발자는 생성자 하나 만들때마다 "의존성을 관리하고 주입해야하는" 일을 수행해야합니다.
        이는 매우 번거롭고 실수가 발생할 수 있는 일이기 때문에 DI Container에서 제공해주는 어노테이션을 통해 쉽고 안전하게 의존성을 주입할 수 있게 됩니다.
        
        또한 Spring framework의 DI Container는 CGLIB를 통해 싱글톤으로 빈 객체 인스턴스를 관리해주기 때문에 메모리를 낭비를 줄일 수 있습니다.

<br>



[참고](https://tecoble.techcourse.co.kr/post/2021-04-27-dependency-injection/) 