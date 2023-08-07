## HTTP 헤더2 - 캐시와 조건부 요청

### 캐시
* 캐시가 없을 때
    * 데이터가 변경되지 않아도 계속 네트워크를 통해서 데이터를 다운로드 받아야 한다.
    * 인터넷 네트워크는 매우 느리고 비싸다.
    * 브라우저 로딩 속도가 느리다.
    * 느린 사용자 경험
* 캐시 적용
    * 캐시 덕분에 캐시 가능 시간동안 네트워크를 사용하지 않아도 된다.
    * 비싼 네트워크 사용량을 줄일 수 있다.
    * 브라우저 로딩 속도가 매우 빠르다.
    * 빠른 사용자 경험
* 사용
    * 예) 서버 측에서 요청 결과 값과 헤더에 cache-control: max-age=60 적용을 하면 클라이언트 측에서 브라우저 캐시에 응답 결과를 저장을 한다.

### 검증 헤더와 조건부 요청
* 검증 헤더 (서버)
    * 캐시 데이터와 서버 데이터가 같은지 검증하는 데이터
    * Last-Modified , ETag
* 조건부 요청 헤더 (웹브라우저, 클라이언트)
    * 검증 헤더로 조건에 따른 분기
    * If-Modified-Since: Last-Modified 사용
    * If-None-Match: ETag 사용
    * 요청 후 서버 반환 값 
        * 조건이 만족하면 200 OK
        * 조건이 만족하지 않으면 304 Not Modified
* Last-Modified, If-Modified-Since
    * 서버가 요청 결과 값과 헤더에 데이터 최종 수정일을 같이 보내주는 방식
    * 웹 브라우저에서 브라우저 캐시에 데이터 최종 수정일을 저장
    * 캐시 시간 초과 시 브라우저가 데이터 최종 수정일을 포함하여 서버에 다시 요청
    * 서버에서 비교 후 데이터가 수정 되지 않았으면 HTTP Body 없이 헤더 데이터만 302 Not Modified 를 함께 보내준다.
    * 브라우저 캐시에 있는 응답 결과를 재사용, 헤더 데이터 갱신
* Last-Modified, If-Modified-Since 장점
    * 캐시 유효 시간이 초과해도, 서버의 데이터가 갱신되지 않으면
    * 304 Not Modified + 헤더 메타 정보만 응답(바디X)
    * 클라이언트는 서버가 보낸 응답 헤더 정보로 캐시의 메타 정보를 갱신
    * 클라이언트는 캐시에 저장되어 있는 데이터 재활용
    * 결과적으로 네트워크 다운로드가 발생하지만 용량이 적은 헤더 정보만 다운로드
    * 매우 실용적인 해결책
* Last-Modified, If-Modified-Since 단점
    * 1초 미만(0.x초) 단위로 캐시 조정이 불가능
    * 날짜 기반의 로직 사용
    * 데이터를 수정해서 날짜가 다르지만, 같은 데이터를 수정해서 데이터 결과가 똑같은 경우
    * 서버에서 별도의 캐시 로직을 관리하고 싶은 경우
        * 예) 스페이스나 주석처럼 크게 영향이 없는 변경에서 캐시를 유지하고 싶은 경우
* ETag, If-None-Match
    * ETag(Entity Tag)
    * 캐시용 데이터에 임의의 고유한 버전 이름을 달아둠
        * 예) ETag: "v1.0", ETag: "a2jiodwjekjl3"
    * 데이터가 변경되면 이 이름을 바꾸어서 변경함(Hash를 다시 생성)
        * 예) ETag: "aaaaa" -> ETag: "bbbbb"
    * 진짜 단순하게 ETag만 보내서 같으면 유지, 다르면 다시 받기
* ETag, If-None-Match 장점
    * 진짜 단순하게 ETag만 서버에 보내서 같으면 유지, 다르면 다시 받기!
    * 캐시 제어 로직을 서버에서 완전히 관리
    * 클라이언트는 단순히 이 값을 서버에 제공(클라이언트는 캐시 메커니즘을 모름)
    * 예)
        * 서버는 배타 오픈 기간인 3일 동안 파일이 변경되어도 ETag를 동일하게 유지
        * 애플리케이션 배포 주기에 맞추어 ETag 모두 갱신
* 정리
    * 검증 헤더 (Validator) - 서버
        * ETag: "v1.0", ETag: "asid93jkrh2l"
        * Last-Modified: Thu, 04 Jun 2020 07:19:24 GMT
    * 조건부 요청 헤더 - 클라이언트, 웹브라우저
        * If-Match, If-None-Match: ETag 값 사용
        * If-Modified-Since, If-Unmodified-Since: Last-Modified 값 사용

### 캐시 제어 헤더
* Cache-Control
    * 캐시 지시어
    * Cache-Control: max-age
        * 캐시 유효 시간, 초 단위
    * Cache-Control: no-cache
        * 데이터는 캐시해도 되지만, 항상 원(origin) 서버에 검증하고 사용
    * Cache-Control: no-store
        * 데이터에 민감한 정보가 있으므로 저장하면 안됨
        * 메모리에서 사용하고 최대한 빨리 삭제
* Pragma
    * 캐시 제어(하위 호환)
    * 사용 X
* Expires
    * 캐시 만료일 지정(하위 호환)
    * 예) expires: Mon, 01 Jan 1990 00:00:00 GMT
    * 지금은 더 유연한 Cache-Control: max-age 권장
    * Cache-Control: max-age와 함께 사용하면 Expires는 무시

### 프록시 캐시
* 원 서버에 직접 접근 시 응답 속도가 오래 걸리는 경우가 있어, 중간의 프록시 캐시 서버를 두고 요청하는 방식
* Cache-Control
    * 캐시 지시어(directives) - 기타
    * Cache-Control: public
        * 응답이 public 캐시에 저장되어도 됨
    * Cache-Control: private
        * 응답이 해당 사용자만을 위한 것임, private 캐시에 저장해야 함(기본값)
    * Cache-Control: s-maxage
        * 프록시 캐시에만 적용되는 max-age
    * Age: 60 (HTTP 헤더)
        * 오리진 서버에서 응답 후 프록시 캐시 내에 머문 시간(초)

### 캐시 무효화
* Cache-Control
    * no-cache
        * 데이터는 캐시해도 되지만, 항상 원 서버에서 검증하고 사용(이름에 주의!)
    * no-store
        * 데이터에 민감한 정보가 있으므로 저장하면 안됨
        * 메모리에서 사용하고 최대한 빨리 삭제
    * must-revalidate
        * 캐시 만료후 최초 조회시 원 서버에 검증해야함
        * 원 서버 접근 실패시 반드시 오류가 발생해야함 - 504(Gateway Timeout)
        * must-revalidate는 캐시 유효 시간이라면 캐시를 사용함
    * no-cache 와 must-revalidate 의 차이
        * no-cache 의 경우 원 서버와의 네트워크가 단절이 됐을 경우 중간의 프록시 캐시에서 임의로 **200 OK** 를 보내는 경우가 있을 수 있음.
        * must-revalidate 의 경우 원 서버와의 네트워크가 단절이 됐을 경우 항상 오류가 발생해야 함 (504 Gateway Timeout 에러 발생)  
* Pragma: no-cache
    * HTTP 1.0 하위 호환