### SPRING.JPA.OPEN-IN-VIEW 로그 오류 해결하기 [출처](https://mand2.github.io/spring/spring-boot/1/)


* 문제발생
    * ```
      aWebConfiguration$JpaWebMvcConfiguration : spring.jpa.open-in-view is enabled by default. Therefore, database queries may be performed during view rendering. Explicitly configure spring.jpa.open-in-view to disable this warning     
      ```

* 문제 이유
    * Spring Boot 에서는 spring.jpa.open-in-view 를 true 로 설정하고 있는데, 이는 OSIV 측면에서 매우 부적절하다고 함. 
        * OSIV 란, 영속성 관리를 말한다. [출처](https://stylishc.tistory.com/150)
    * 즉, 확장성 측면에서 볼 때 false로 해야 하는데 true로 하고 있어 warning 경고 사인이 뜨는 거라고.
    
* 해결 방법
    * application.properties 에서 설정하기
        * ```
          spring.jpa.open-in-view=false
          ```