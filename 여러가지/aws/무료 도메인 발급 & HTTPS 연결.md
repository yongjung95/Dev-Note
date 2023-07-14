### 무료 도메인 발급 & HTTPS 연결 

* 무료 도메인 발급 [참고](https://loy124.tistory.com/347), [참고](https://loy124.tistory.com/347)
    * 나는 freenom 을 이용해서 무료 도메인을 발급받았다. 기간은 1년인데 갱신할 수 있다고 들었다. 
    * aws 와 연동을 해주어서 완성.
    * NS에 써있는 각각의 네임서버들을(4개) 각각 freenom 에 저장해주면 된다.

* HTTPS 연결 [참고](https://happiestmemories.tistory.com/48), [참고](https://it-eldorado.tistory.com/117)
    1) EC2 내부에 SSL 인증서를 설치하고 서비스하는 방법 (일반적인 기존 방식)
    2) AWS 에서 제공하는 인증서 관리 서비스인 ACM(AWS Certificate Manager)을 ACM 통합서비스와 연동하여 적용하는 방법
    * 나는 2번째 방법을 이용하였다.