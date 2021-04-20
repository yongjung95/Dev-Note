## REST

* REST 란, ```웹에 존재하는 모든 자원(이미지, 동영상, DB자원)에 고유한 URI를 부여해 활용``` 하는것으로, 자원을 정의하고
    자원에대한 주소를 지정하는 방법론을 의미한다고 한다.
  


* 이런 REST 의 형식을 따른 시스템을 RESTful 이라고 부른다.
    * HTTP URI 를 통해 자원을 명시하고 HTTP Method 를 통해 해당 자원의 대한 CRUD Operation 을 적용한다.
  

  
* CRUD Operation , HTTP Method
    * Create : POST (자원 생성)
    * Read : GET (자원의 정보 조회)
    * Update : PUT (자원의 정보 업데이트)
    * Delete : DELETE (자원 삭제)
    

* REST 구성요소
    * 자원(Resource) , URI
        * 모든 자원은 고유한 ID를 가지고 ID는 서버에 존재하고 클라이언트는 각 자원의 상태를 조작하기 위해 요청을 보낸다. HTTP 에서 이러한 자원을 구별하는 ID는 ```'Students/1'``` 같은 HTTP URI 이다.
    * 행위(Verb) , Method
        * 클라이언트는 URI 를 이용해 자원을 지정하고 자원을 조작하기 위해 Method 를 사용한다. HTTP 프로토콜에서는 GET , POST , PUT , DELETE 같은 Method 를 제공한다.
    * 표현(Representation)
        * 클라이언트가 서버로 요청을 보냈을 때 서버가 응답으로 보내주는 자원의 상태를 Representation 이라고 한다. REST 에서 하나의 자원은 JSON , XML , TEXT , RSS 등 여러형태의 Representation으로 나타낼수 있다.