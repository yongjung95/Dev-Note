### JAR 와 WAR 차이 [참고](https://hye0-log.tistory.com/27)

* 기본적으로 JAR, WAR 모두 Java 의 jar 옵션 (java -jar)을 이용해 생성된 압축(아카이브) 파일로, 애플리케이션을 쉽게 배포하고 동작시킬 수 있도록 관련 파일(리소스, 속성 파일 등)을 패키징 한 것이다.


* JAR
    * JAVA 어플리케이션이 동작할 수 있도록 자바 프로젝트를 압축한 파일
    * Class (JAVA 리소스, 속성 파일), 라이브러리 파일을 포함함
    * JRE(JAVA Runtime Environment)만 있어도 실행 가능함 (java -jar 프로젝트네임.jar)


* WAR
    * Servlet / Jsp 컨테이너에 배치할 수 있는 웹 애플리케이션(Web Application) 압축파일 포맷
    * 웹 관련 자원을 포함함 (JSP, Servlet, JAR, Class, XML, HTML, Javascript)
    * 사전 정의된 구조를 사용함 (WEB-INF, META-INF)
    * 별도의 웹서버(WEB) or 웹 컨테이너(WAS) 필요
    * 즉, JAR 파일의 일종으로 웹 애플리케이션 전체를 패키징 하기 위한 JAR 파일이다.


* 결론 
    * JAR, WAR 파일 애플리케이션 리소스를 패키징 하는 방법에 차이가 있을 뿐,
    * 뭘 사용해야 하느냐는 개발자의 판단에 따를 뿐이다.
    * 꼭 WAR 를 사용해야만 하는 이유(꼭 JSP 를 사용하여 화면을 구성해야 한다 / 외장 WAS 를 이용할 계획이 있다)가 아니라면 뭘 사용할지에 대한 완벽한 해답은 없는 듯하다.
    * SpringBoot 에서 가이드하는 표준은 JAR 이니까 JAR 를 사용하여 서비스하는 것도 괜찮은 선택이라고 본다.


* 내가 개발한 food-travel 은 JSP 를 사용해서 WAR 를 사용하였다.