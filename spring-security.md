# Spring Security

인증\(Authorization\) 을 담당하며 우리가 상상 할 수 있는 모든 Identity 확인을 지원한다.   
설령, 지원하지 않는 Identity 확인 방식이 있다면 만들 수 있다.

#### AuthenticationManager

AuthenticationManager 는 어떤 인증 방식이 와도 수용할 수 있도록 작성되어 있다.  
\* 어떠한 요청이 와도 \(HTTP/RPC/Async message\)  
\* 어떠한 인증 방식이 와도 \(Token/ID,PW/인증서\)

```java
public interface AuthenticationManager {
    Authentication authenticate(Authentication authentication) 
        throws AuthenticationException;
}
```

AuthenticationManager 의 구현체로 AuthenticationProvider 가 실제 인증을 담당한다. 처리하지 못하는 인증 방식이 있을 때 해당 처리를 부모에 맡길 수 있다.

DB 나 LDAP 같은 DataSource 를 연동해서 인증 처리도 가능하다. 이를 위해 스프링은 DaoAuthenticationProvider 를 제공하며, 인증의 위임은 UserDetailsService 인터페이스에 맡긴다.

```java
public interface UserDetailsService {
    UserDetails loadUserByUsername(String username)
        throws UsernameNotFoundException;
}
```

사용자 정보를 담고 있는 UserDetails 객체를 반환하면 되고 해당 객체는 패스워드/계정 만료 여부/사용자 권한 등을 캡슐화 하고 있다.



