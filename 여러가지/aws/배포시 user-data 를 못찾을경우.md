### 배포시 user-data 를 못찾을경우 [출처](https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/WindowsGuide/ec2-windows-user-data.html)

* 스프링부트를 인스턴스에서 실행 시에 에러가 발생하면서 작동이 안되서 해맸는데, 
    * http:169.265.169.265/latest/user-data 였나? 이런식의 주소에서 404 에러가 발생한다고 로그가 발생하는데
    
* 이거때문에 안됐던건지는 잘 모르겠지만 이 문제는 위에 링크대로 했더니 해결이 되었다.