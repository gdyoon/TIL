# Spring Security

인증\(Authorization\) 을 담당하며 우리가 상상 할 수 있는 모든 Identity 확인을 지원한다.   
설령, 지원하지 않는 Identity 확인 방식이 있다면 만들 수 있다.

#### Authentication Manager

AuthenticationManager 는 어떤 인증 방식이 와도 수용할 수 있도록 작성되어 있다.  
\* 어떠한 요청이 와도 \(HTTP/RPC/Async message\)  
\* 어떠한 인증 방식이 와도 \(Token/ID,PW/인증서\)

```java
public interface AuthenticationManager {
    Authentication authenticate(Authentication authentication) 
        throws AuthenticationException;
}
```



