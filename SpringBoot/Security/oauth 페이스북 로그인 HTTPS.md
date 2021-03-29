### oauth 페이스북 로그인 HTTPS

* 페이스북은 로컬 개발인 ```localhost:8080``` 을 제외하고 자신이 만든 도메인을 등록 할시에는 무조건
HTTPS 를 사용해야만 페이스북 로그인을 사용할 수 있다.
  

* 나는 AWS 에서 제공하는 ACM 을 이용하여 HTTPS 를 구현 했는데, 그래도 사용이 되지 않았다.


* 알고보니 내가 만든 웹사이트에서 페이스북 로그인을 누르게 되면 Redirect URI 가 HTTP 로 호출이 되었던것이다.


* 그래서 application.properties 에서 
    * ``` 
      spring.security.oauth2.client.registration.facebook.redirect-uri=https://www.food-travel.tk/login/oauth2/code/facebook
      ```
      
    * 다음과 같이 redirect-uri 의 값을 지정해두었더니 정상적으로 동작이 된다.
