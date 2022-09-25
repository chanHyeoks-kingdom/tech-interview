# TCP가 뭐에요?


## 답변: <br>
        TCP는 전송 제어 프로토콜입니다. 우리가 통신을 할때 IP만 쓴다면 우리가 보내는 데이터가 신뢰할 수 없고, 연결성을 가질 수 없으며 어떤 프로그램에서 보내고 받을 데이터인지 구분할 수 없게
        되어버립니다. 그래서 PORT 식별을 위한 번호가 담긴 TCP 세그먼트라는걸 전송 데이터에 감싸는데 이에 대한 규칙을 TCP라고 합니다.


<img src="https://velog.velcdn.com/images%2Fsms8377%2Fpost%2F9405abd5-f92a-4b82-8568-ef068b0259a6%2Fimage.png" width="800" height="200"/>


<br>
<br>

### 추가 질문: IP만 이용해 통신했을때 문제가 생긴다는거죠? 어떤 문제가 있고 TCP를 쓰면 어떻게 해결이 되나요?



    "비연결성, 비신뢰성, 프로그램 구분의 한계"라는 3가지 문제를 해결할 수 있습니다.
    
#### (1) [비연결성]
        IP만 가지고 통신할때는 상대방이 내 패킷을 받았는지 알 방법이 없습니다. IP 정보만 적어서 서버로 패킷을 던졌을 때 서버가 잠깐 꺼져있던 상태인 경우가 그렇습니다.
        
        [해결]
        그래서 TCP는 3 Way Handshake라는 방법을 통해서 
        
        1. 클라이언트가 서버한테 접속좀 해줘~ 하고 (SYN)을 보낸다.                    [SYN]
        2. 서버가 옥케이~(ACK)해주면서 나도 너한테 접속 하게 해줘(SYN)을 보낸다        [SYN+ACK]
        3. 클라이언트가 그걸 보고 옥케이~ (ACK)하면 그 떄부터 데이터 전송              [ACK]
        
        이렇게 서로 연결되었음을 확인 하고 데이터를 보내는데, 요즘은 최적화 되서
        클라이언트가 옥케이(ACK)~를 보낼때 데이터도 같이 보내줍니다.
        
        단 여기서 "연결"은 물리적인 연결이 아니라 개념적인 연결입니다.
        물리적으로 라우터들이 연결됨을 확인한게 아니라 서로 "연결된 상태"임을 확인하는 개념입니다.
        
        
#### (2) [비신뢰성]
        비신뢰성은 "패킷 전달 순서"에 대한 문제입니다. "나는 개발자중에 왕 최찬혁 입니다"라는 메시지를 보낼 때
        데이터의 사이즈를 끊어서 읽어옵니다. 예를 들면 "나는 개", "발자중에", "왕 최찬혁", "입니다" 처럼 데이터를 읽어오는데
        저희가 저 패킷들을 전송하는 과정에서 "같은 경로"를 쓰는게 아니라 그때그때 다른 경로를 쓰기  먼저 출발한 패킷의 경로 사이에 있는 광케이블을 
        맷돼지가 끊어먹는다거나 하는 경우 "먼저 출발한 패킷"이 늦게 도착할 수 있습니다. 그렇게 순서가 바뀌면
        
        "나는 개" "입니다" "발자중에" "왕 최찬혁"이라는 메시지가 되어버립니다. 이는 심각하고 중대한 사안이기에 
        저 패킷들의 순서를 보장해서 "신뢰성 있는 전송"을 만들어줘야 합니다.
        
        [해결]
        위 첨부한 TCP Header를 보면 32bit 짜리 Sequence number라는게 있습니다. 수신자는 저걸 보고 데이터 청크들을 붙여주기만 하면 됩니다.
        
        그외 에러체크를 위한 checksum등을 이용하기도 합니다. 에러 검증을 하고 잘 보내진 정보에 대해서 ACK Flag를 set(1) 해주고
        Acknowlegment number에 수신자가 받은 sequence number에 1을 더한 값을 넣어서 보내줍니다.
        
        
#### (3) [프로그램 구분의 한계]       
        포트 번호를 이용해 구분할 수 있게 되었습니다. 시작 포트 번호는 내가 만든 소켓의 포트 번호가 들어가고
        목적지 포트 번호는 HTTP기준 80, HTTPS는 443등의 번호가 들어갑니다.


결론은 위와 같은 방법으로 IP 통신의 문제를 TCP를 이용해 해결할 수 있습니다. 



레퍼런스: https://www.youtube.com/watch?v=BEK354TRgZ8
         https://www.techtarget.com/searchnetworking/definition/TCP-IP    