## 답변:
<br>
OSI 모델은 1980년대에 ISO에서 채택되어 당시 통신 회사들이 사용했던 프로토콜입니다. 네트워크 통신을 위한 최초의 표준 모델인데 간단히 말하면 그냥 권고안 같은 역할입니다.
현재는 대부분 TCP/IP 4계층 모델을 써서 요즘의 네트워크 아키텍처와 매핑되는 경우는 거의 없지만 네트워크 아키텍처를 설명하는 수단으로 자주 사용됩니다. <br>
<br>

### 추가 질문: 7계층은 어떻게 이루어져 있나요?



    7계층에 대해서 설명하려면 편지를 쓰는 과정을 통해 설명할 수 있을 거 같습니다.
    
#### (1) [Application 계층 (7Layer)]
<img src="https://yimgf-thinkzon.yesform.com/docimgs/public/1/2/1145/1144203.jpg" width="200" height="200"/>

        Application 계층은 제가 쓴 편지지를 의미합니다. Client가 특정 Application을 이용해서, 서버로 보내고 싶은 데이터를 입력하고 가공하는 과정입니다.
        예시를 들면 제가 네이버에 접속을 하면 크롬 브라우저가 HTTP Message를 만들어서 네이버 서버로 보내는데, "네이버 페이지 줘"라는 요청을 
        HTTP라는 편지지에 작성하는 것이므로 HTTP는 Application 계층이라고 할 수 있습니다.
    
<br>

#### (2) [Presentation 계층 (6Layer)]
<img src="https://blog.kakaocdn.net/dn/zJ0iT/btrhzRZVyg3/rp3AJkmGcz7gnN8RkfESFK/img.png" width="200" height="200"/> <img src="https://miro.medium.com/max/1400/1*elzAdHViXbVDSXpe_VhTHw.png" width="500" height="200"/>

        Presentation계층은 말 그대로 표현하는 계층입니다. 
        이 과정에서 어플리케이션에서 작성된 텍스트에 대해 "암호-복호화, 압축, 인-디코딩"등의 작업이 이루어집니다.
        "즉, 사용자에게 보낼 Text(HTTP Message와 같은 텍스트)가 컴퓨터에게 어떻게 표현될지 정하는 계층입니다"
        
        ** 이때 암호화든 인코딩이든, 이런 표현 형식은 내가 보내는 요청을 받는 서버와 동기화가 되어있어야 합니다.
        
        
#### (3) [Session 계층 (5Layer)]    
<img src="http://mstatic2.e-himart.co.kr/contents/goods/00/14/59/45/58/0014594558__HPH-WS990R__M_640_640.jpg" width="200" height="200"/> <img src="https://cdn.pixabay.com/photo/2015/05/23/07/47/walkie-talkie-780306__480.jpg" width="200" height="200"/>
       
       Session 계층은 통신 회선의 생성, 유지, 종료 관리 결정합니다. 
       전화기처럼 서로 통신하게 할건지, 무전기처럼 한명씩 말할 수 있게 할건지, 아니면 특정인만 수신하게 할건지등을 결정하고
       회선을 열어주고 닫아주는 역할을 합니다.
       


#### (4) [Transport 계층 (4Layer)]   
       [크게 두가지 역할이 있는데 첫째는 포트번호를 정해주는 것입니다.]
       편지에 내 포트번호를 넣어주고 (송신자)
       HTTP(80), HTTPS(443)중 어떤 것으로 보낼지를 결정합니다. (수신자)
       
       [두번째는 TCP와 UDP에 대해서 정의하는 것입니다.]
       HTTP/1.1이나 HTTP/2의 경우 TCP를 기반으로 하지만
       HTTP/3같은 경우는 UDP를 사용하기 떄문에 이런 부분을 정의해줍니다.

       (+ TCP는 편지를 보내고 나서 잘 받았는지 확인 해주는 장점이 있고 (등기 우편)
       UDP는 편지를 보내고 나서 잘 받았는지 관심이 없습니다.)


#### (5) [Network 계층 (3Layer)]   
      이 편지가 어느 경로로 전달되어야 하는지에 대한 내용을 담고 있다.
      충남 -> 천안시 -> 동남구 -> 봉명동과 관련된 내용이며 실제 IP의 경우
      27.117.254.112 같은 내 IP가 그 예로 볼 수 있습니다.


#### (6) [Data Link 계층 (2Layer)]  
      네트워크 계층을 통해 우리 아파트까지 편지가 왔다고 했을때 
      몇동 몇호로 와야 하는지에 대한 내용을 담고 있는게 DataLink 계층입니다.
      이러한 식별을 위해 필요한게 MAC 주소인데, 이걸 Data Link 계층에서 넣어줍니다.

#### (7) [Physical 계층 (1Layer)]  
      편지는 그냥 보내면 되지만, 컴퓨터의 '텍스트'는 전기 신호로 바꿔서 보내줘야 합니다.
      Physical 계층에서는 여태까지 전처리한 데이터를 전기신호로 바꿔서 내보내는 역할을 합니다다.

여러 라우터(지역 거점 우체국)들을 거쳐서 수신측에게 내가 쓴 편지가 전달 되면

이렇게 encapsulation을 통해 전처리한 데이터를 
수신측에서는 역순으로 decapsulation 과정을 거쳐 열어봅니다.

<br>
<br>




## 관련 설명 

    80년대에 ISO(국제 표준 단체)에서 발표한 
    - OSI Model은 네트워크 통신을 위한 최초의 표준 모델이다. [참조1]
    - OSI Model은 7가지 추상적인 개념을 이용해 통신에 필요한 시스템을 분류함
    - 분류내용 Physical, Data Link, Network, Transport, Session, Presentation, and Application. 
    


<br><br><br><br><br><br>
[참조1]. https://www.imperva.com/learn/application-security/osi-model/  - What is the OSI Model (Imperva.com) <br>
[참조1]. https://www.forcepoint.com/ko/cyber-edu/osi-model              - What is the OSI Model? (forcepoint.com)
