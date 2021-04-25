## Querydsl

* ### 장점
    * 대표적으로 type-safe 이다.
        * java 의 enum, constant 를 이용해 type 이 의미하는 바를 한눈에 알아볼 수 있음
            ``` 
            -- *.xml 
            select * from store where type = 1  -- type이 의미하는게 무엇일까??
            ```
            ```
            // querydsl
            selectFrom(store).where(store.type.eq(storeConstant.영업중))  -- 타입이 의미하는 바를 알 수 있다.
            ```          

    * 잘못된 쿼리를 xml 에 작성 후 build 해도 에러는 발생하지 않는다.
    실제 쿼리를 호출해야 그제서야 에러가 발생한다. 이런 문제를 사전에 방지 할 수 있다.
      
    * column 의 타입을 알 수 있다.
    

* ### 사용방법
    1. Table 별로 Entity 를 생성한다.
    2. APT 를 이용하여 Entity 기반으로 querydsl plugin 을 실행시키면 prefix ```Q```가 붙는 큐클래스가 생성된다. 
       
        ``` Store -> QStore```
       * APT 란?
       * Annotation Processing Tool 의 약자이다.
       * Annotation 이 있는 코드기준으로 새로운 파일을 만들 수 있고 complie 기능도 가능하다.
    
    3. 생성된 큐클래스를 사용하여 type-safe 한 querydsl 을 생성한다.
    4. querydsl 을 실행하면 내부에서 JPQL 을 생성한다.
       * JPQL 이란?
            - Java Persistence Query Language 의 약어이다.
            - JPA 의 일부로 독립적인 객체지향 쿼리 언어이다.
            - 관계형 데이터베이스의 엔티티에 대한 쿼리를 만드는데 사용된다.
            - 데이터베이스에 다이렉트로 연결되지 않고 JPA 엔티티에 대해서 작동한다.
    5. SQL 을 생성하여 Database 에 직접 쿼리를 사용하여 조회한다.
        
        ``` Querydsl -> JPQL -> SQL ```