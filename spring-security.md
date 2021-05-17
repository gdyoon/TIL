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

사용자 정보를 담고 있는 UserDetails 객체를 반환하면 되고 해당 객체는 패스워드/계정 만료 여부/사용자 권한 등을 캡슐화 하고 있으며, 이 과정에서 인가에 사용되는 GrantedAuthority 타입이 함께 반환된다.

AccessDecisionManager 인터페이스는 인증 요청자가 어떤 권한을 갖고 있는지 확인하는 핵심적인 역할을 하며 접근 제어에 관한 결정을 반환한다.

Spring Security 는 두개의 큰 계층 구조로 나뉘어져 있고 인증/인가를 모두 처리해준다.   
최상위에 루트 인터페이스가 존재하고 이 루트 인터페이스가 자신과 비슷한 일을 하는 여러 객체 인스턴스를 생성한다.   
이 객체 인터페이스 들은 인증/인가 에 대한 세부적인 처리들을 위임받고 인증/인가에 대한 연쇄적인 처리를 진행한다. \(책임 연쇄 패턴 ㅡ Chain of Responsibilities\)



