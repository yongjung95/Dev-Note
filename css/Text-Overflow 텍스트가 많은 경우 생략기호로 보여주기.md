### Text-Overflow 텍스트가 많은 경우 생략기호로 보여주기
  
* text-overflow 를 구현하기 위한 조건
    * i. width 또는 height 가 고정적일 것
    * ii. overflow: hidden; 을 사용해 영역을 감출 것
    * iii. 아래줄로 내려가는 것을 막기위해 white-space: nowrap 등이 필요

* ```
  div p {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  }
  ```
  
* text-overflow 속성은 display 속성이 블럭 형태인 경우에만 적용됩니다. 
  즉, inline의 경우는 적용되지 않습니다. 이를 적용하기 위해서는 반드시 아래와 같이 display를 block 또는 inline-block과 같이 설정해야만 적상적으로 작동합니다.
  * ``` 
    body span {
    display: block;  // inline-block으로 설정 필요
    }
    ```