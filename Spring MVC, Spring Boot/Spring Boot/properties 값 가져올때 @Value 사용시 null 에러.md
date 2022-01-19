### properties 값 가져올때 @Value 사용시 null 에러 [출처](https://thingsthis.tistory.com/326)

* 스프링에서는 정적변수로 선언된 변수에는 injection 할 수 없다고 한다. 
  그렇기 때문에 static 을 삭제 한 다음 그에 맞게 사용하거나 꼭 static 으로 해야겠다 싶으면...

* ```
    private static String tmpUploadPath; 
    
    @Value("${file.upload.path.tmp}") 
    public void setTmpUploadPath(String path) { 
        tmpUploadPath = path; 
    }

  ```
  
    * 이런식으로 사용을 해야한다.