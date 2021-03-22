### oauth 페이스북 로그인 데이터 삭제 [출처](https://become-a-developer.tistory.com/entry/%EB%82%B4%EA%B0%80-%EB%A7%8C%EB%93%A0-%EC%9B%B9%ED%8E%98%EC%9D%B4%EC%A7%80%EC%97%90%EC%84%9C-%ED%9A%8C%EC%9B%90%ED%83%88%ED%87%B4%EC%8B%9C-%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%B6%81-%EA%B6%8C%ED%95%9C-%ED%95%B4%EC%A0%9C-%ED%95%98%EA%B8%B0)

* oauth 로 페이스북 로그인 후 회원 탈퇴를 진행이 필요한 경우. 
  
* 요청 url 은 ``` 'https://graph.facebook.com/{user-id}/permissions?access_token={token}'``` 이런식으로 요청하면 되는데,
로그인 할 당시에 user-id 와 토큰을 따로 저장해두어야 한다. 
  
* url 요청은 ``` DELETE ``` 로 요청을 해야 가능하다. ``` GET ``` 으로 요청하니까 안됐음.

* 
  ``` 
  try {
          HttpComponentsClientHttpRequestFactory factory = new HttpComponentsClientHttpRequestFactory();
          factory.setConnectTimeout(5000); //타임아웃 설정 5초
          factory.setReadTimeout(5000);//타임아웃 설정 5초
          RestTemplate restTemplate = new RestTemplate(factory);

          HttpHeaders header = new HttpHeaders();
          HttpEntity<?> entity = new HttpEntity<>(header);
          String url = null;

          url = "https://graph.facebook.com/{user-id}/permissions?access_token={token};
          UriComponents uri = UriComponentsBuilder.fromHttpUrl(url).build();

          //이 한줄의 코드로 API를 호출해 MAP타입으로 전달 받는다.
          ResponseEntity<Map> resultMap = restTemplate.exchange(uri.toString(), HttpMethod.DELETE, entity, Map.class);
          result.put("statusCode", resultMap.getStatusCodeValue()); //http status code를 확인
          result.put("header", resultMap.getHeaders()); //헤더 정보 확인
          result.put("body", resultMap.getBody()); //실제 데이터 정보 확인

          //데이터를 제대로 전달 받았는지 확인 string형태로 파싱해줌
          ObjectMapper mapper = new ObjectMapper();
          jsonInString = mapper.writeValueAsString(resultMap.getBody());

  } catch (HttpClientErrorException | HttpServerErrorException e) {
          result.put("statusCode", e.getRawStatusCode());
          result.put("body"  , e.getStatusText());
          System.out.println("dfdfdfdf");
          System.out.println(e.toString());

  } catch (Exception e) {
          result.put("statusCode", "999");
          result.put("body"  , "excpetion오류");
          System.out.println(e.toString());
  }
  ```
  
* RestTemplate 을 사용한 실제 프로젝트내에 구현한 코드
  
* 페이스북 개발자 document 를 찾아봤는데 정확하게 나와 있지 않아서 구글링 하다가 그나마 비슷한 php 코드를 발견했다.