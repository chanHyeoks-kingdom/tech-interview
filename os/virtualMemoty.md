### 가상 메모리의 핵심은 보조 기억 장치 (HDD ..) 이다.


옛날에는 메모리가 작아서 프로그램의 크기가 메인 메모리보다 큰 경우가 있었는데요.
이를 해결하기 위해서 프로그램을 잘라서 순서대로 메인 메모리에 로딩하는 오버레이라는 방법을 사용했습니다.

이런 오버레이 방식도 어느정도 한계가 있어서 등장한게 "가상 메모리"라는 방법입니다.
가상 메모리는 애플리케이션 실행에 필요한 최소한의 코드만 메모리에 올려서 메모리를 더 커 보이게 하는 방법입니다. 
이게 가능한 이유는 실행에 필요한 최소한의 코드 외의 것들은 HDD 같은 보조 저장장치에 저장해두기 때문인데요.
MMU라는 장치를 이용해 이런 과정을 관리합니다.