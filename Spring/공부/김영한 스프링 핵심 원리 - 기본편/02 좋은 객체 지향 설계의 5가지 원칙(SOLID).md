### 좋은 객체 지향 설계의 5가지 원칙(SOLID)

* SRP 단일 책임 원칙 
  * 한 클래스는 하나의 책임만 가져야 한다.
    * 하나의 책임이라는 것은 모호하다. 클 수 있고, 작을 수 있다. 문맥과 상황에 따라 다르다. 
    * `중요한 기준은 변경`이다. 변경이 있을 때 파급 효과가 적으면 단일 책임 원칙을 잘 따른 것 
    * 예)UI 변경, 객체의 생성과 사용을 분리
  * 변경을 했을 때 다른 곳에 영향이 없으면 `단일 책임 원칙`을 잘 지켰다고 할 수 있다.


* ⭐️ OCP 개방-폐쇄 원칙 ⭐️
    * 소프트웨어 요소는 확장에는 열려 있으나 변경에는 닫혀 있어야 한다
    * 이런 거짓말 같은 말이? 확장을 하려면, 당연히 기존 코드를 변경?
        * 다형성을 활용해보자
        * 인터페이스를 구현한 새로운 클래스를 하나 만들어서 새로운 기능을 구현
        * 지금까지 배운 역할과 구현의 분리를 생각해보자


* LSP 리스코프 치환 원칙
    * 인터페이스의 규약을 지켜야하는 것.
        * 예) 자동차 인터페이스의 엑셀은 앞으로 가라는 기능, 뒤로 가게 구현하면 LSP 위반, 느리더라도 앞으로 가야함


* ISP 인터페이스 분리 원칙
    * 특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다
        * 자동차 인터페이스 -> 운전 인터페이스, 정비 인터페이스로 분리
        * 사용자 클라이언트 -> 운전자 클라이언트, 정비사 클라이언트로 분리
        * 분리하면 정비 인터페이스 자체가 변해도 운전자 클라이언트에 영향을 주지 않음
    * 인터페이스가 명확해지고, 대체 가능성이 높아진다.


* ⭐️ DIP 의존관계 역전 원칙 ⭐️
    * 쉽게 클라이언트가 구현 클래스에 의존하지 말고, 인터페이스에 의존하라는 뜻
    * 구현에 의존하지 말고 역할에 의존 해야한다는 것이다
    * 추상화에 의존하고 구체화에 의존하면 안된다
	