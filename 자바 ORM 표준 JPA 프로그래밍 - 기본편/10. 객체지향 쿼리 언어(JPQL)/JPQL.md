## JPQL

* ### JPQL 문법
    * ```select m from Member as m where m.age > 18```
        * 엔티티와 속성은 대소문자 구분O (Member, age)
        * JPQL 키워드는 대소문자 구분X (SELECT, FROM, where)
        * 엔티티 이름 사용, 테이블 이름이 아님(Member)
        * 별칭은 필수(m) (as는 생략가능)
    * COUNT, SUM, AVG, MAX, MIN 다 사용가능
    * GROUP BY, HAVING, ORDER BY 다 사용가능
    

* ### TypeQuery, Query
    * TypeQuery : 반환 타입이 명확할 때 사용
        * ``` TypedQuery<Member> query = em.createQuery("SELECT m FROM Member m", Member.class); ```
    * Query : 반환 타입이 명확하지 않을 때 사용
        * ```Query query = em.createQuery("SELECT m.username, m.age from Member m"); ```
    
    
* ### 결과 조회 API
    * ```query.getResultList()``` : 결과가 하나 이상일 때, 리스트 반환
        * 결과가 없으면 빈 리스트 반환
    * ```query.getSingleResult()``` : 결과가 정확히 하나, 단일 객체 반환
        * 결과가 없으면 :  javax.persistence.NoResultException 에러 발생
        * 둘 이상이면 : javax.persistence.NonUniqueResultException 에러 발생
    * Spring JPA 사용시에는 Optional 타입으로 사용 가능
    
* ### 파라미터 바인딩 
    * 이름 기준
        ```
        SELECT m FROM Member m where m.username=:username 
        query.setParameter("username", usernameParam);
        ```
    * 위치 기준 (사용X)
        ```
        SELECT m FROM Member m where m.username=?1 
        query.setParameter(1, usernameParam);
        ```
