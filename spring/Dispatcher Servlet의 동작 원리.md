## Dispatcher Servlet의 동작 원리가 뭐에요??

<img width="975" alt="567856784" src="https://user-images.githubusercontent.com/68278903/194102754-dfb6861c-13a8-401c-a02c-ce3f7f615ec7.PNG">


```
 (1) Dispathcer Servlet는 front-controller 패턴이라고 해서 컨트롤러 앞에서 HTTP를 통해 들어오는 모든 Request를 받아줍니다.
 (2) 서블릿이 파싱해준 reqeust url을 보고 'HandlerMapping' 정보를 조회해 해당 컨트롤러 객체를 받아온다.
 (3) 해당 컨트롤러 객체에 맞는 어댑터를 조회해서 해당 컨트롤러에 맞는 처리를 해주고
 (4) 핸들러에서 실질적인 요청 처리, Model을 만들고 HTTP가 보여줄 View Name 지정등의 처리를 해준 다음 Dispatcher Servlet에게 반환해줌
 (5) ViewResolver는 String 형태로 넘어온 viewName을 받고, Model에 저장된 데이터를 이용해 View 객체 생성
 (6) View는 모델과 viewName을 받아서 화면에 그려주는 역할을 함
 

```

A. 먼저 디스패처 서블릿이 http 요청을 받아주구여, 핸들러 매핑 정보를 조회해서 해당 요청에 매핑되는 핸들러를 찾습니다.
이후에 핸들러 어뎁터 정보를 또 조회해서 해당 핸들러에 맞는 어뎁터를 찾은 뒤에 실제 핸들러를 호출 해줍니다.
핸들러는 실제적인 비즈니스 로직이 동작하구여, Model등을 만들고 View name 지정등의 처리를 해준 다음에 Dispatcher Sevlet에게 다시 넘겨줍니다.
Dispatcher은 viewResolver를 이용해 String으로 넘어온 viewname을 받고 해당 view를 호출하는데
호출된 view는 Model을 이용해서 화면을 그립니다.


### 추가 질문1. MVC 구조를 사용했을 때는 사용하지 않았을 때와 다르게 어떤 이점이 있을까요
```
JSP와 서블릿 만으로 개발하면 공통 로직으로 인한 중복 처리의 문제가 발생합니다. 예를들어 dispatcher.forward(request, response);를 해주는 부분 같은 경우가 그렇습니다.
이를 Frontcontroller등을 이용해 해결해줄 수 있습니다.
  ```

A. MVC를 이용하지 않으면 발생하는 문제는 코드의 유지보수성이 현저히 떨어집니다.
  
### 추가 질문2. SPRING MVC의 힘이 뭔가요?
```
기존 서블릿, JSP를 이용한 MVC의 문제인 dispatcher.forward(request, response);등의 중복 처리를 Frontcontroller등을 이용해 해결해줄 수 있습니다.
또 View를 분리하고 모델을 이용하고 또 어뎁터 패턴등을 이용해서 컨트롤러를 작성하는 사람이 별 다른 고민 없이 MVC를 구현토록 프레임워크를 만들었습니다.
```

A. 사실 servlet과 jsp를 이용해서 MVC Pattern을 구현하는건 매우 어려운 일입니다. adapter 패턴등의 적용 처럼 어려운 과제들이 있는데요.
Spring MVC의 Dispatcher Servlet은 FrontController의 역할을 그 외에 Handler Mapping이나 Handler Adapter Mapping등이 MVC 구현을 위한 역할을 대신 해주기 떄문에
개발자는 MVC에 대한 어려운 내용을 고민하지 않아도 Controller를 쉽게 구현할 수 있게 됩니다.


### 추가 질문3. MVC는 무조건 좋은 구조일까요?
```
MVC 패턴은 View와 model 사이의 의존성이 높다는 점 때문에 어플리케이션이 커질수록 복잡해지고 유지보수가 어렵다는 단점이 있습니다.
MVVN 패턴이라는 것도 사용하는 것으로 알고 있습니다.
```
A. MVC Pattern의 약점은 view와 model의 의존성이 높습니다. 이를 해결해주기 위해 MVVN pattern등을 이용하기도 합니다.
