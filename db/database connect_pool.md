## 데이터베이스_커넥션_풀

### 데이터베이스 커넥션 풀을 사용하는 이유가 몬가요?

        (1) 만약에 하나의 DB 컨넥션만 사용한다면 여러 요청에 대해 병목 현상이 발생한다.
        (2) 그래서 성능상의 이점을 위해 여러개의 DB 컨넥션을 사용하는데
        (3) 매번 DB 접근마다 JDBC Driver를 로드하고 커넥션 객체를 생성해서 연결하는 과정은 (종료도 해야함) 비효율적이다.
        (4) 그래서 톰캣같은 WAS가 실행될때 미리 DB와 연결된 connection 객체를 생성해서 pool에 저장해둔다.
        (5) 클라이언트에서 DB 리소스 관련한 요청이 오면 미리 만들어둔 connection 객체를 리턴해주면 된다.
        
-
        [주의점]
        (1) 요청이 과하게 몰리면 메모리가 버티지 못하고 서버가 터질 수 있다.
        (2) 그렇다고 커넥션 풀을 너무 적게 잡으면 성능적인 측면에서 낭비가 발생한다.
