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