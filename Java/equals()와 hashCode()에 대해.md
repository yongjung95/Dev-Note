### equals()와 hashCode()에 대해

* ####equals() 와 hashCode()
    * hashCode 
        * 객체를 식별하는 하나의 정수값을 말한다. Object 의 hashCode() 메소드는 객체의 메모리 번지를 이용해서 해시코드를 만들어 리턴하기 때문에 객체 마다 다른 값을 가지고 있다.
    * equals 메소드와 hashcode 메소드는 Object 클래스의 메소드입니다.
    * Object 는 상속 관계상 가장 위에 있기 때문에 (모든 클래스가 Object 를 상속)
    * 어떤 객체라도 Object 의 메소드인 equals 와 hashcode 를 사용할 수 있게 됩니다.

    ![img.png](equals()와%20hashCode()에대해.png)


* ### equals() 재정의
    * #### 예제 
      ![img_3.png](equals()와%20hashCode()에대해_2.png)
    * Object 에 정의된 equals 를 확인하면 
      
        ![img_2.png](equals()와%20hashCode()에대해_1.png)
      
    * 단순히 Object 의 == 로 비교하는 것을 확인할 수 있다.
    * 어떻게 객체가 동일한지 비교할 수 있을까?
        * 새롭게 정의한 클래스에서는 두 객체가 같은 객체임을 의미하는 equals 메소드를 재정의 하면 문제를 해결할 수 있다.
        * 이때, 우리는 아직 Object 에서 정의된 hashcode 를 사용하기 때문에 두 객체의 hashCode 는 다르다.
          equals()를 재정의한다면 ```side effect(부작용)``` 를 줄이기 위해서 hashCode()도 재정의하는것이 좋다.
          

* 정리    
    ![img.png](equal()와%20hashCode()에%20대해_3.png)
    * ``` equals 메소드에 의해 true가 나오는 두 객체의 hashcode는 같아야 한다. ```


* 출처
    * [Java equals()와 hashCode()에 대해](https://nesoy.github.io/articles/2018-06/Java-equals-hashcode)
    * [[기초부터자바] hashcode란? hashcode와 equals의 관계(2) {오버라이드, 재정의 문제 포함}](https://m.blog.naver.com/travelmaps/220931531769)