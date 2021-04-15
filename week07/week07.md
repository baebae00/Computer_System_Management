# 20200994 배서은
**컴퓨터시스템관리 7주차 실습일지**

---
#### 7주차에는 
1. 리눅스에서 사용하는 셸에 대해 이해
2. 셸 스크립트를 이용하여 간단한 스크립트 작성
3. 예약 작업 설정
---

## 1. 실습과제 결과

* ### **유용한 bash script 를 하나 검색하여, 유용한 이유, 해당 스크립트 설명, 실행 결과 작성**
  
* ### **bash script (Delete a File)** <br>
    
  * bash script (Delete a File)가 유용한 이유

    ```
    'rm' 명령어를 사용해 특정 파일을 삭제하는 기존의 방식은 디렉터리의 포함관계, 예를들어 '~/code/temp/*' 와 같이 해당 파일이 포함되어 있는 경로를 알아야 정확한 제거가 가능하다.
    그러나 이번 과제를 수행하면서 생성한 'delete_file.sh' bash script를 사용한다면 제거하고 싶은 파일명만 입력하면 자동적으로 삭제 가능하다는 점에서 유용하다고 생각했다. 
    ```

  * bash script (Delete a File) 설명

    ```
    'rm' 명령어는 파일을 제거하는 데에 사용된다.
    bash script 중 rm의 역할을 대신해 즐 'delete_file.sh' 를 생성해 보았다.
    이 bash는 사용자로부터 삭제할 파일명을 입력받아 제거해주는 셸이다.
    '-i' 옵션은 파일을 제거하기 전에 사용자로부터 권한을 얻는 데 사용된다.
    ```

  * bash script (Delete a File) 실행 결과

    - bash 실행 후 지워질 파일(delete.sh) 미리 생성

        ![지워질것2](https://user-images.githubusercontent.com/77660379/114817152-74ace100-9df4-11eb-9a66-28ed00b528aa.JPG)

    - '이 파일은 지워질 파일' 이라는 주석 추가

        ![지워질것3](https://user-images.githubusercontent.com/77660379/114817198-8b533800-9df4-11eb-8670-c3d36267ea3c.JPG)
    
    - 사용자로부터 파일이름을 입력받아 제거해주는 bash 생성

        ![만든것1](https://user-images.githubusercontent.com/77660379/114817223-95753680-9df4-11eb-8a5b-a1e94608f33b.JPG)

     - bash 실행 후 제거된 'delete.sh' 파일

        ![만든것2](https://user-images.githubusercontent.com/77660379/114817293-af167e00-9df4-11eb-8747-f5e5deb60baa.JPG)

## 2. 실습과제 Review

* ### **새로 배운 내용**

```
1. Shell
    => 사용자의 명령을 해석하여 커널에 전달
       Kernel & Shell

       Shell Script
       -> 명령어 집합
          과정이 복잡하여 하나라도 빠지면 문제가 생기거나, 매일 또는 주기적으로 해야 하는 명령의 집합
          시스템을 사용하여 환경 설정하는 경우, 애플리케이션을 설치할 경우, 매일 점검해야 하는 시스템 상태 체크 등


2. Shell - bash
    => bash (Bourne Again SHell)
          1998년, 브라이언 폭스Brain Fox가 발표한 유닉스 셸
          우분투에서 기본으로 사용하는 셸

       bash 특징
        -> alias 기능 (명령어 단축 기능)
           History 기능
           연산 기능
           Job Control 기능
           자동 이름 완성 기능
           프롬프트 제어 기능
           명령 편집 기능


3. 작업예약 - cron & at
     => 매일 새벽 5시에 중요한 log 파일을 백업해야 한다면?
        퇴근 후, 시스템을 최신 패키지로 업데이트 하고, 재부팅하고 싶다면?

        cron
        -> 주기적으로 반복되는 일을 자동으로 실행할 수 있도록 시스템 작업을 예약하는 것
           cron과 관련된 데몬(서비스)은 crond, 관련 파일은 /etc/crontab
            /etc/crontab의 형식
            -> 분 시 일 월 요일 사용자 실행명령

        at
        -> 일회성 작업을 예약하는 것
```

* ### **문제가 발생하거나 고민한 내용 + 해결 과정**

- **사용자 추가, 사용자 패스워드 출력 오류**

    ![오오류1](https://user-images.githubusercontent.com/77660379/114819652-c6f00100-9df8-11eb-91c0-07dca32d84d4.JPG)

    ![오오류2](https://user-images.githubusercontent.com/77660379/114819695-d707e080-9df8-11eb-9854-aa260334fe94.JPG)

    ![오류3](https://user-images.githubusercontent.com/77660379/114819756-e71fc000-9df8-11eb-80ba-53ae40bf05b8.JPG)

    ```
    문제발생 및 고민한 내용 : 사용자 추가, 사용자 패스워드 출력에 오류 발생

    해결 과정 : 사용자 계정과 패스워드를 입력하고 존재 여부를 확인하는 과정에서 문제가 발생함
               -> vi adduser-script.sh 에서 ${userList[i]}, ${passwdList[i]} 코드를 작성하였기 때문에 bash 시켰을 때 정보가 차례로 출력되어야 하는데 출력되지 않음
               -> 중괄호, 소괄호 입력에서 실수가 있었던 것으로 예상됨
               -> 문제를 한번에 해결하기 위해 sh 파일 자체를 제거하고 강의를 다시 돌려보며 재생성함
               -> 문제가 해결되고 파일 역시 제대로 저장된 것을 확인함
    ````

* ### **참고할 만한 내용**

  * 리눅스 text모드, gui모드 설정

    [리눅스 모드 변경하기](https://shsec.tistory.com/7)

    ```
    7버전 이하에서는 text모드와 gui모드설정을 /etc/inittab 파일을 수정하여 설정하였지만,
    7버전 이후에서는 systemctl 명령어를 사용하여 변경이 가능하다.

    systemctl get-default
    => 현재 모드 확인

    systemctl set-default multi-user.target
    => text 모드로 변경

    systemctl set-default graphical.target
    => gui 모드로 변경
    ```

  * 30 bash script examples

    [bash script ex]](https://linuxhint.com/30_bash_script_examples/#t21)

    ```
    Bash 스크립트는 셸 명령 실행, 여러 명령 실행, 관리 작업 사용자 지정, 작업 자동화 수행 등 다양한 용도로 사용할 수 있다.
    이번 과제에서 생성한 파일제거 bash script 이외에도 유용한 많은 scipt들이 있으니 필요한 셸을 추가적으로 생성하고자 링크를 첨부하였다.
    ```

* ### **회고 (+,-,!)**
```
1. 뿌듯했던 점 (+)
    => 지금까지 해왔던 실습 중 가장 즐겁게 임한 것
          -> 오류가 많이 발생했던 지난 주차와 달리 이번 주차는 코딩 과정이 많아 비교적 수월했고 재미있었다.
             특히 이번에 생성한 파일 제거 bash script는 정말 유용하게 사용될 것이라 생각한다.
             파일을 삭제할 때마다 상위 디렉터리, 그 경로까지 입력하는 과정에서 오류가 난 적이 한두번이 아니다.
             오타를 내기도 하고, 슬래쉬(/)를 두번 누르기도 하고 띄어쓰기에 실수를 내기도 했었기 때문이다.
             그러나 이번에 설치한 bash script로 보다 정확하고 편리하게 파일을 삭제시킬 것을 생각하니 벌써 다음 주차 수업이 기대된다.
       
2. 보완할 점 (-)
    => 띄어쓰기, 괄호 입력에 주의하기
      -> 프로그래밍을 할 때마다 느끼는 점이지만 코딩은 띄어쓰기, 문자 하나하나가 정말 중요한 것 같다.
         이번 실습이 즐거웠지만 그래도 python이나 C++, java와는 또 다른 느낌이었다.
         중괄호는 기존 프로그래밍 방식에 사용되지 않다보니 이번 실습에서 중괄호, 소괄호 구분하는 데에 있어 오류가 났다.
         익숙하지 않더라도 항상 배우려는 자세로 차근차근 임해야함을 느꼈다.
 
3. 꼭 기억할 점 (!) 
    => cron과 at
         cron : 주기적인 작업을 예약
         at : 일회성 작업을 예약