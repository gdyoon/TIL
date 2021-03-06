# OAuth



OAuth 는 1.0/1.0a/2.0 3가지 버전이 존재하며, 2.0 이 최신이다.  
Open Authorization 의 약자로 "토큰 기반 인가" 의 표준이다.

#### 토큰 사용의 장점

개인정보\(ID/PW\) 의 노출을 최소화함에 따라 얽매이지 않게 하고 잘못된 클라이언트가 올바른 사용자의 계정을 잠글 수 없도록 보장한다.

OAuth 는 인증 보다는 인가에 해당하는 프로토콜이다.   
즉, 인증과는 다른 프로세스에서 처리되어야 하며, 인증이 처리된 후에는 OAuth 가 제어권을 넘겨 받는다.

#### **OAuth 용어**

* 클라이언트: iOS/Android 와 같은 모바일 기기 또는 브라우저. 리소스 접근에 대한 요청을 생성하는 주체
* 자원 소유자 \(Resource Owner\) : 접근하고자 하는 리소스에 대해 가장 큰 권한을 갖는 사용자
* 자원 서버 \(Resource Server\) : 리소스를 관리하는 서버
* 인가 서버 \(Authorization Server\) : Access Token 을 발급하며 인가 서버가 자원 서버라 볼 수 있음

#### OAuth 시나리오

1. 서드파티 웹 사이트에서 "페이스 북 로그인" 클릭
2. ID/PW 입력 및 submit 시, 클라이언트에 권한 인가 동의 여부 확인
3. 페이스북의 Authorization Server 호출.
4. Authorization code 를 Access Token 으로 교환.
5. Access Token 을 저장소에 저장한
6. 페이스북의 Resource Server 에 자원 요청



