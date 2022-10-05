### 질문 1. 스프링 기반의 API 서버를 개발했다고 쓰여있는데 REST API 아시나요?
      REST는 아키텍처 스타일입니다. 아키텍처 스타일은 "제약 조건의 집합"을 의미하는데요.
      따라서 REST API는 "REST라는 제약조건의 집합을 충족하는 API라고 생각합니다."
      
      REST 안에 포함되는 제약조건들은 client-server, stateless, cache, uniform interface, layered system등이 있습니다. 
      제가 생각하는 중요한 제약조건은 stateless와 uniform interface가 있다고 생각하는데요.
      stateless는 Server가 Client에 대한 어떠한 상태도 저장하지 않음을 의미합니다.
      이로인해 클라이언트는 인증을 위한 Token이나 Key등을 Request에 포함시켜 전송해야 하게 됩니다.
      

##### 질문 1-1. 그럼 사용자가 요청 할때마다 Token을 넣어서 보내줘야 하는거네요? 그럼 오히려 불편한거 아니에요? 왜 굳이 그렇게 만들어야 하나요?

      만약에 Stateful한 제약조건을 허용하게 되어버리면 서버가 여러개일때 사용자에 대한 정보를 매번 동기화 해줘야합니다.
      예를들면 대규모 환경에서 동일한 웹서버를 다수 배치해 로드밸런싱을 할 때 각 서버가 Client의 상태와 세션을 공유할 수 있는 Redis와 같은 별도의 시스템이 필요하게 됩니다. 
      
      
##### 질문 1-2. Redis에 대해 잘 아시나요?

    아뇨 잘 모르고 인메모리 디비라는 것만 알고 있습니다.
    

##### 질문 1-3. 아 .. 그런가요? 아까 unfiform interface도 중요하다고 한 거 같은데 왜 그런가요?

      REST 아키텍처 스타일에서 uniform interface를 제외한 나머지 것들은 HTTP만 잘 따라도 지킬 수 있지만 uniform inerface도 아키텍처 스타일이어서요. 안에 제약조건들이 있는데
      그 중에 HATEOAS와 self-descriptive message라는 조건들을 충족시키지 못하는걸로 알고 있습니다. 그래서 REST API를 구현하려면 이 부분을 신경써야 한다고 알고 있습니다.
      
      
##### 질문 1-4. HATEOAS랑 self-descriptive message가 무슨 의미에요?
      (1) HATEOAS는 하이퍼 링크를 이용해 애플리케이션 상태 전이가 일어나야 한다는 조건이고
      (2) self-descriptive message라는건 보내는 데이터가 어떤 것인지도 명확히 설명해 줘야 한다는 얘기입니다. 예를들면 jsonPatch등에 대한 명세가 있습니다.
      [아래 학습용 사진 첨부]
      
<img width="310" alt="45674567456745672" src="https://user-images.githubusercontent.com/68278903/192554241-9bc67a5a-d3e3-4808-b05c-5d0ee971aeaa.PNG"> <img width="480" alt="4756745674567" src="https://user-images.githubusercontent.com/68278903/192549422-26fddfa3-834d-40dc-8bfa-1ea5ee8f77f9.PNG">

      
##### 질문 1-5. Uniform-interface를 안쓰면 어떻게 되는데요?
      Uniform Interface를 지켜주지 못하면 로이 필딩이 처음 HTTP/1.0을 구현할때 가장 고민했던 "독립적인 진화"를 보장할 수 없게 됩니다.
      
