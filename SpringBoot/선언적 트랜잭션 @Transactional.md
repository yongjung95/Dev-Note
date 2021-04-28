## 선언적 트랜잭션 @Transactional

* ### 트랜잭션이란 ?
    * 데이터베이스의 상태를 변경시키는 작업 또는 한번에 수행되어야하는 연산들을 의미한다.
    * 트랜잭션 작업이 끝나면 Commit 또는 Rollback 되어야한다.
    ![img.png](사진파일/트랜잭션의%20성질.png)
      


* ### @Transactional
    * 스프링에서 지원하는 선언적 트랜잭션이다. Spring boot 에서는 별도의 설정이 필요 없으며, 클래스 또는 메소드에 선언할 수 있다.
    
        ```
        @Transactional
        public List<PostDto> getList() {
        
        }
        ```
    

* ### @Transactional 옵션
    * propagation
        * 트랜잭션 동작 도중 다른 트랜잭션을 호출할 때, 어떻게 할 것인지 지정하는 옵션이다
        
            ![img.png](사진파일/트랜잭션%20propagation.png)
        
    * isolation
        * 트랜잭션에서 일관성없는 데이터 허용 수준을 설정한다.
            ![img.png](사진파일/트랜잭션%20isolation.png)
    * noRollbackFor=Exception.class
        * 특정 예외 발생 시 rollback 하지 않는다.
        * 트랜잭션 작업 중 런타임 예외가 발생하면 롤백한다. 반면에 예외가 발생하지 않거나 체크 예외가 발생하면 커밋한다.
        * 하지만 원한다면 체크예외지만 롤백 대상으로 삼을 수 있다. rollbackFor 또는 rollbackForClassName 속성을 이용해서 예외를 지정한다.    
    * rollbackFor=Exception.class
        * 특정 예외 발생 시 rollback 한다.
        * rollbackFor 속성과는 반대로 런타임 예외가 발생해도 지정한 런타임 예외면 커밋을 진행한다.
    * timeout
        * 지정한 시간 내에 메소드 수행이 완료되지 않으면 rollback 한다. ( -1일 경우 timeout 을 사용하지 않는다.)
    * readOnly
        * 트랜잭션을 읽기 전용으로 설정한다.
        * 특정 트랜잭션 안에서 쓰기 작업이 일어나는 것을 의도적으로 방지하기 위해 사용된다. insert,update,delete 작업이 진행되면 예외가 발생한다.
    

* ### 출처
    * [[Spring Boot] 선언적 트랜잭션 @Transactional](https://bamdule.tistory.com/51)