### oauth 구글 로그인 데이터 삭제 [출처](https://developers.google.com/identity/protocols/oauth2/web-server#httprest_8)

* 프로그래밍 방식으로 토큰을 취소하기 위해 애플리케이션은 토큰을 요청 ```https://oauth2.googleapis.com/revoke``` 
  하고 매개 변수로 포함해야한다.
  
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
        UriComponents uri = null;
        ResponseEntity<Map> resultMap = null;

        header.add("Content-type","application/x-www-form-urlencoded");
        url = "https://oauth2.googleapis.com/revoke?token="+userDto.getToken();
        uri = UriComponentsBuilder.fromHttpUrl(url).build();
        resultMap = restTemplate.exchange(uri.toString(), HttpMethod.POST, entity, Map.class);

        //이 한줄의 코드로 API를 호출해 MAP타입으로 전달 받는다.

        result.put("statusCode", resultMap.getStatusCodeValue()); //http status code를 확인
        result.put("header", resultMap.getHeaders()); //헤더 정보 확인
        result.put("body", resultMap.getBody()); //실제 데이터 정보 확인

        //데이터를 제대로 전달 받았는지 확인 string형태로 파싱해줌
        ObjectMapper mapper = new ObjectMapper();
        jsonInString = mapper.writeValueAsString(resultMap.getBody());

  } catch (HttpClientErrorException | HttpServerErrorException e) {

            result.put("statusCode", e.getRawStatusCode());
            result.put("body"  , e.getStatusText());
            System.out.println(e.toString());

  } catch (Exception e) {

            result.put("statusCode", "999");
            result.put("body"  , "excpetion오류");
            System.out.println(e.toString());

  }

  System.out.println(jsonInString);
  ```
  
* RestTemplate 을 사용한 실제 프로젝트내에 구현한 코드

* 토큰은 액세스 토큰 또는 새로 고침 토큰 일 수 있습니다. 
  토큰이 액세스 토큰이고 해당하는 새로 고침 토큰이있는 경우 새로 고침 토큰도 취소됩니다.

* 해지가 성공적으로 처리 된 경우 응답의 HTTP 상태 코드는 200입니다. 오류 조건의 경우 HTTP 상태 코드 400가 오류 코드와 함께 반환됩니다.