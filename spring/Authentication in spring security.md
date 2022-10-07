
스프링 시큐리티에서 인증은 어떻게 이루어지나요?

```
HttpRequest 요청이 들어오면 AuthenticationManager에서 회원ID를 UserDetailsService에 넘기고 
회원 ID를 DB에서 조회하여 조회된 회원객체를 소유한 UserDetails를 생성합니다. 
그리고 UserDetails를 다시 AuthenticationManager로 보내서 ‘인증’을 완료합니다.
```
