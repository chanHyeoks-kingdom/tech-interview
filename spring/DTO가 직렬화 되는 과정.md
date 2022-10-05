## DTO가 직렬화 되는 과정이 어떻게 되나요?


```
@를 사용해 viewResolver 대신에 HttpMessageConvert가 대신 동작하는데요
기본 객체의 경우 MappingJackson2HttpMessageConverter가 동작해 json으로 직렬화 해서
HTTP Body에 문자 내용을 직접 반환해줍니다.
```
