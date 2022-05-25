### JSONObject 배포시 발생하는 오류 처리방법  [출처](https://velog.io/@godkimchichi/NoClassDefFoundError-JSONObject)

 * 로컬에서는 JSONObject 매핑이 잘 됐었는데, 서버에 올리니 에러 발생할 때
 * CustomJsonUtil 을 만들 때, 아래의 클래스에서 import 해서 만들었기 때문

    ```
    <dependency>
	    <groupId>org.springframework.boot</groupId>
	    <artifactId>spring-boot-configuration-processor</artifactId>
	    <optional>true</optional>
    </dependency>
    ```