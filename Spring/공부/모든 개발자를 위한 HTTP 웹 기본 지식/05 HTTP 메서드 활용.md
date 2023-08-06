### HTTP 메서드 활용

* HTTP API - 컬렉션 (주로 사용)
  * POST 기반 등록
  * 서버가 리소스 URI 결정

* HTTP API - 스토어
  * PUT 기반 등록
  * 클라이언트가 리소스 URI 결정

* HTML FORM 사용
  * 순수 HTML + HTML form 사용
  * GET, POST 만 지원

* 참고하면 좋은 URI 설계 개념
  * 문서(document)
    * 단일 개념(파일 하나, 객체 인스턴스, 데이터베이스 row)
    * 예) /members/100, /files/star.jpg
  * 컬렉션(collection)
    * 서버가 관리하는 리소스 디렉터리 
    * 서버가 리소스의 URI를 생성하고 관리 
    * 예) /members 
  * 스토어(store)
    * 클라이언트가 관리하는 자원 저장소 
    * 클라이언트가 리소스의 URI를 알고 관리 
    * 예) /files 
  * 컨트롤러(controller), 컨트롤 URI 
    * 문서, 컬렉션, 스토어로 해결하기 어려운 추가 프로세스 실행 
    * 동사를 직접 사용 
    * 예) /members/{id}/delete