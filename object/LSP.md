 
 
[진짜 좋은 참조 블로그](https://inpa.tistory.com/entry/OOP-%F0%9F%92%A0-%EC%95%84%EC%A3%BC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EB%8A%94-LSP-%EB%A6%AC%EC%8A%A4%EC%BD%94%ED%94%84-%EC%B9%98%ED%99%98-%EC%9B%90%EC%B9%99)
 
```
다시한번 말하지만 어렵게 생각할 필요없이, 너무나도 당연하게 자바를 코딩하면서 사용해온 다형성을 규칙으로서 문서화한 것이 LSP 원칙이라고 보면 된다.

그래서 LSP는 한마디로 다형성을 지원하기 위한 원칙 이라고 딱 잘라 정의할 수 있다.

아무래도 우리는 처음 프로그래밍 언어를 배울때 코드 사용법을 배우지, 코드 설계법을 배우지 않기 때문에 이런식으로 뭔가 학습을 거꾸로 배우는 듯한 느낌이 드는것은 어쩔수 없다고 본다.
```
```
JAVA
void myData() {
	// Collection 인터페이스 타입으로 변수 선언
    Collection data = new LinkedList();
    data = new HashSet(); // 중간에 전혀 다른 자료형 클래스를 할당해도 호환됨
    
    modify(data); // 메소드 실행
}
 
void modify(Collection data){
    list.add(1); // 인터페이스 구현 구조가 잘 잡혀있기 때문에 add 메소드 동작이 각기 자료형에 맞게 보장됨
    // ...
}
```
