## Entity, DTO 바로 알기

* ### Entity 란?
    * Entity 클래스는 실제 DataBase 의 테이블과 1 : 1로 매핑 되는 클래스로, DB의 테이블내에 존재하는 컬럼만을 속성(필드)으로 가져야 한다.
      
    * Entity 클래스는 상속을 받거나 구현체여서는 안되며, 테이블내에 존재하지 않는 컬럼을 가져서도 안된다.
    

* ### Entity 는 Setter 금지😡!!
    

* ### DTO 란?
    * DTO(Data Transfer Object)는 데이터 전송(이동) 객체라는 의미를 가지고 있다. DTO 는 주로 비동기 처리를 할 때 사용한다.
    * ```계층간 데이터 교환을 위한 객체(Java Beans)```이다.
    * ```DB의 데이터를 Service 나 Controller 등으로 보낼 때 사용하는 객체```를 말한다.
    * 즉, ```DB의 데이터가 Presentation Logic Tier 로 넘어올때는 DTO 로 변환되어 오고가는 것```이다.
    * ```로직을 갖고 있지 않는 순수한 데이터 객체```이며, ```getter/setter 메서드만```을 갖는다.
    * 또한 ```Controller Layer 에서 Response DTO 형태로 Client 에 전달```한다.


* ### Entity, DTO Class 분리 이유
  * Entity 와 DTO 를 분리해서 관리해야 하는 이유는 ```DB Layer 와 View Layer 사이의 역할을 분리 하기 위해서```다.
  * Entity 클래스는 ```실제 테이블과 매핑```되어 만일 ```변경되게 되면 여러 다른 클래스에 영향```을 끼치고, DTO 클래스는 ```View 와 통신하며 자주 변경되므로 분리``` 해주어야 한다.
  * 결국 DTO 는 Domain Model 객체를 그대로 두고, 복사하여 다양한 Presentation Logic 을 추가한 정도로 사용하며 Domain Model 객체는 Persistent 만을 위해서 사용해야한다.
    