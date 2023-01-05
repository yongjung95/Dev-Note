### AWS EC2에 Docker로 MySql 띄우기 

* 사전에 `EC2`에 `yum` 과 `docker` 가 설치되어 있어야 한다.
  * 따라 했던 블로그의 주소를 잃어버려 검색을 하길 바란다.
    * `ubuntu 22.04` 에서는 `yum` 말고 `yum4`를 사용하는 것 같음. (`yum4`를 사용하여 작업했음. `yum4`를 키워드로 검색하길 바람.)

* `EC2` 또는 외부에서 접근 시 `docker`의 보안 그룹 포트를 열어줘야 한다.

### [참고]('https://mungiyo.tistory.com/23')