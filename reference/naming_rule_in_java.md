

### 1. 모든 패키지명은 소문자

```
com.sample.package.bluetooth
com.sample.package.wifi
com.sample.package.handler
```

### 2. 클래스(Class) / 인터페이스(Interface)
* 첫 글자는 항상 대문자로 합니다.
* 주로 연관있는 명사로 지정합니다.
* 여러 단어로 이루어진 이름일 경우 단어의 첫 글자를 대문자로 합니다.

```
* class ClassName
* interface InterfaceName
```

### 3. 메서드(Method)
* 첫 글자는 항상 소문자로 합니다.
* 주로 연관있는 동사로 지정합니다.
- 카멜 케이스 

```
public int getName() {
    ...
}

public boolean setName(int n) {
    ...
}

public String findAllName() {
    ...
}
, 단 생성자의 경우 파스칼 케이스
```




### 4. 상수
모든 글자를 대문자로 합니다.
여러 단어로 이루어진 이름일 경우 _로 구분합니다.
```
private static final int MAX;<br>
private static final int MIN;<br>
private static final int MAX_VALUE;<br>
private static final int MIN_VALUE;​<br>

```


