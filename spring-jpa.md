# Spring JPA

자바에는 ORM 이라는 개념이 있다. 관계형 데이터베이스를 사용하기 위한 방법으로 객체 자체가 테이블이 되는 것. 즉 엔티티가 되도록 맵핑시켜주는 프레임워크다.

JPA 는 ORM 기술에 대한 API 명세이다. JPA 를 그대로 쓸 수도 있고 JPA 인터페이스의 구현체인 Hibernate 나 OpenJPA 와 같은  패키지를 쓸 수도 있다. 대게 Hibernate 를 많이 쓰지만, 반드시 사용 할 필요는 없다.

JPA 는 자바에서 RDB 를 어떻게 써야 할지 정의한 방식이지 라이브러리가 아니다.

Spring JPA 를 사용하면서 EntityManager 를 직접 다뤄본적도 있지만, 그럴 필는 없을 것 같다.

### Sprig Data JPA

순수 JPA 대신 Spring Data JPA 가 있어 조금 더 편하게 사용할 수 있다. Repository 인터페이스 규격에 맞춰 메서드 이름을 작명하면 Spring 에서는 해당 이름에 맞는 적절한 쿼리를 생성해서 질의 하는 구현를 만들어주고 이를 Bean 으로 등록해준다.
