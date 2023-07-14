## Commit log 유지하면서 Git Repository 합치기

### 방법
* 옮기고 싶은 `Repository`의 이름을 `sub_repo`, 메인으로 가지고 있고 싶은 `Repository`의 이름을 `main_repo` 라고 하자.

1. `main_repo`를 git clone 받는다.
    ```
    https://dailylifeofdeveloper.tistory.com/193
    ``` 

2. `main_repo`안에서 아래와 같이 `git subtree add --prefix=(해당 Repository 하위의 디렉토리 구조) (옮겨 올 Repository 주소) (옮겨 올 Repository의 branch)` 를 입력한다.
   ```
   git subtree add --prefix=make_sub_reop_file https://github.com/****/sub_repo.git master
   ```
   
3. 새로운 `file`이 생겼는 지 확인하고 `git add -> commit -> push`를 순서대로 진행한다.

4. `git`에 접속하여 확인하고 옮기고 싶은 `Repository` 삭제

- [commit log 유지하면서 Git Repository 합치기](https://dailylifeofdeveloper.tistory.com/193)