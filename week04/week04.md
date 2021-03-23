# 20200994 배서은
**컴퓨터시스템관리 4주차 실습일지**

---
#### 4주차에는 
1. 리눅스 기본 프로그램 사용
2. X 윈도우의 개념 이해
3. 다양한 방법으로 응용 프로그램 설치
4. 다양한 데스크톱 환경 설치
---

## 1. 실습과제 결과

* ### **Server(b)에 GNOME 데스크톱 설치 후, 유용한 프로그램 3개 설치**
  
  **CHECK POINT** <br>
  *우분투에 Chrome을 설치하면 다른 프로그램들을 다운로드하기 보다 유용해진다*

* ### **Chrome 설치** <br>
  
  * Chrome소개

    ```
    우분투에 기본적으로 firefox라는 웹 브라우저가 탑재되어있지만 보다 익숙한 Chrome을 사용하기 위해 설치
    ```

  * Chrome이 유용하다고 생각한 이유

    ```
    aaa
    ```

  - 터미널 창에 크롬 브라우저 패키지 설치용 인증키를 받기 위한 명령어 입력, 크롬 웹 브라우저 패키지를 다운로드 받을 PPA를 sources.list.d 에 추가

    ![chrome1](https://user-images.githubusercontent.com/77660379/112141098-3b7bb980-8c18-11eb-8b55-81a70df88ce9.JPG)

  - 패키지 리스트 업데이트

    ![chrome2](https://user-images.githubusercontent.com/77660379/112141161-4d5d5c80-8c18-11eb-9cc2-f4f0f55bf851.JPG)
    
  - 크롬 설치

    ![chrome3](https://user-images.githubusercontent.com/77660379/112141200-5b12e200-8c18-11eb-8784-19209fdf17c5.JPG)
  
  - 크롬 설치를 위해 생성했던 파일 제거

    ![chrome4](https://user-images.githubusercontent.com/77660379/112141312-7aaa0a80-8c18-11eb-9550-584efb76e85f.JPG)

  - 크롬 설치 완료

    ![chrome설치완료](https://user-images.githubusercontent.com/77660379/112141393-93b2bb80-8c18-11eb-8833-d9105c14b633.JPG)

    ![완료](https://user-images.githubusercontent.com/77660379/112141487-ae853000-8c18-11eb-92d3-87587b88938d.JPG)


* ### **Visual Studio Code 설치** <br>
  - lolcat -h

    ![option](https://user-images.githubusercontent.com/77660379/111276383-a3f7f300-867a-11eb-807f-aa18dd25fb11.JPG)

    ```
    lolcat 사용을 시작하기 전에 사용 가능한 옵션을 알고 다음 명령을 사용하여 도움을 받아야 함
    ```
  - 실행 결과 no.1

    ![실행1](https://user-images.githubusercontent.com/77660379/111276537-c984fc80-867a-11eb-8224-d785f36730d4.JPG)

    ```
    1) # ps | lolcat
    2) # cal | lolcat
    ```

  - 실행 결과 no.2

    ![실행2](https://user-images.githubusercontent.com/77660379/111276733-ffc27c00-867a-11eb-9229-bfa957f0af25.JPG)

    ```
    figlet 명령어 사용
    # figlet <문자> | lolcat
    figlet : (일반 화면 캐릭터로 구성된) 큰 글자를 표시하는 유틸리티
    ```

 ### **Kakaotalk 설치** <br>
  - lolcat -h

    ![option](https://user-images.githubusercontent.com/77660379/111276383-a3f7f300-867a-11eb-807f-aa18dd25fb11.JPG)

    ```
    lolcat 사용을 시작하기 전에 사용 가능한 옵션을 알고 다음 명령을 사용하여 도움을 받아야 함
    ```
  - 실행 결과 no.1

    ![실행1](https://user-images.githubusercontent.com/77660379/111276537-c984fc80-867a-11eb-8224-d785f36730d4.JPG)

    ```
    1) # ps | lolcat
    2) # cal | lolcat
    ```

  - 실행 결과 no.2

    ![실행2](https://user-images.githubusercontent.com/77660379/111276733-ffc27c00-867a-11eb-9229-bfa957f0af25.JPG)

    ```
    figlet 명령어 사용
    # figlet <문자> | lolcat
    figlet : (일반 화면 캐릭터로 구성된) 큰 글자를 표시하는 유틸리티
    ```

## 2. 실습과제 Review
* ### **새로 배운 내용**
```
1. 사용자 정보 확인 /etc/passwd
    => '사용자이름:비밀번호:사용자ID:그룹ID:추가정보:홈디렉터리:로그시제공되는셸'
       추가정보는 선택적 입력 (이름:방번호:직장전화번호:집전화번호:기타)프로세스 관리

2. 그룹 정보 확인 /etc/group
    => '그룹이름:비밀번호:그룹ID:보조그룹사용자'
        보조그룹사용자 : 이 그룹을 주 그룹이 아닌 보조 그룹으로 사용하는 사용자의 목록
        여러 명이면 쉼표로 구분

3. 파일과 디렉터리는 소유권(ownership)과 허가권(permission)이 있음
     => 소유권 : 누가 해당 파일 또는 디렉터리를 생성 및 관리할 수 있는가?
        허가권 : 해당 파일 또는 디렉터리를 읽거나 쓰거나 실행할 수 있는가?

4. 파일 소유권
     => 파일 소유권을 변경하는 명령어
            -> chown ubuntu mydata.txt          // mydata.txt 파일의 소유자를 ubuntu 사용자로 변경
               chown ubuntu.ubuntu mydata.txt   // 파일 그룹도 ubuntu 그룹으로 변경
               chgrp ubuntu mydata.txt          // 그룹만 ubuntu 그룹으로 변경

5. 파일 허가권
     => 파일 허가권을 변경하는 명령어
        소유자, 그룹, 그 외 사용자 별로 구분하여 관리
        root 사용자 또는 해당 파일의 소유자만 실행 가능
        read, write, execute
            -> chmod 777 mydata.txt             // 모든 사용자가 mydata.txt 파일을 읽고, 쓰고, 실행할 수 있음
               chmod u+x mydata.txt             // 소유자에게 실행 권한을 허가(+)
        tar
            -> Tape ARchive
               tar 로 묶여지기 전 파일들의 속성, 심볼릭 링크, 디렉토리 구조 등을 그대로 가져갈 수 있음

6. 링크 파일
     => 하드 링크 hard link
         -> ln <원본파일><링크파일명>
         심볼릭 링크 symbolic link 또는 소프트 링크 soft link
         -> ln -s <원본파일><링크파일명>
```

* ### **문제가 발생하거나 고민한 내용 + 해결 과정**

- **notice.txt 파일의 중복 생성**
    ![1](https://user-images.githubusercontent.com/77660379/111340982-703dbd00-86bc-11eb-80a1-591ea49caad3.JPG)

    ![2](https://user-images.githubusercontent.com/77660379/111341062-821f6000-86bc-11eb-99b2-1850deca9686.JPG)

    ![3](https://user-images.githubusercontent.com/77660379/111341131-93686c80-86bc-11eb-8511-d381cb41140f.JPG)

    ![삭제시도](https://user-images.githubusercontent.com/77660379/111341217-a713d300-86bc-11eb-9eb7-fa94bb250f8c.JPG)

    ![오](https://user-images.githubusercontent.com/77660379/111341301-bd219380-86bc-11eb-9894-8e507ba6fc98.JPG)

    ![다중](https://user-images.githubusercontent.com/77660379/111341392-d1fe2700-86bc-11eb-8f7e-bb2810f9b85f.JPG)

    ![4](https://user-images.githubusercontent.com/77660379/111341522-ef32f580-86bc-11eb-833e-7a565eb5b4b7.JPG)

    ```
    문제발생 및 고민한 내용 : notice.txt 파일에 wq 불가

    해결 과정 : 'E:35: No previous regular expression' 오류 발생
               -> 'E:35' 오류에 대한 의미 구글링했으나 정확한 문제가 무엇인지 알 수 없었음
               -> txt 파일에 내용을 적을 수 있을 때까지 notice.txt 파일을 계속해서 생성했으나 여전히 해결되지 않음
               -> 터미널 창을 닫고 다시 터미널 창을 열어 skel 디렉터리를 비우려고 시도했으나 불가능
               -> notice.txt 파일에 접근하니 또다시 오류 발생
               -> 오류창을 자세히 읽어보니 'vim -r notice.txt' 명령어를 통해 skel 디렉터리를 비울 수 있다는 사실을 알게 됨
               -> 중복 생성된 notice.txt.* 파일들을 'vim -r notice.txt' 명령어로 삭제
               -> skel 디렉터리를 비운 상태에서 새로운 notice.txt 파일을 생성해 문제 해결
    ````

- **명령어 설치 오류**

    ![실행오류](https://user-images.githubusercontent.com/77660379/111339578-37e9af00-86bb-11eb-839a-f83049249185.JPG)

    ![실행오류해결](https://user-images.githubusercontent.com/77660379/111339728-55b71400-86bb-11eb-880c-2bb60ad9d5c3.JPG)

    ![실행2](https://user-images.githubusercontent.com/77660379/111276733-ffc27c00-867a-11eb-9229-bfa957f0af25.JPG)

    ```
    문제발생 및 고민한 내용 : figlet 명령어를 이용해 'I love CSM' 를 출력하려 시도했으나 오류 발생

    해결 과정 : figlet 명령어는 기본적으로 패키지 안에 포함되어 있는 것이 아니기 때문에 따로 설치가 필요
               -> # apt install figlet 을 콘솔창에 입력하여 figlet을 사용할 수 있는 환경을 구축함
    ```

* ### **참고할 만한 내용**
```
리눅스 패키지 설정 명령어 rpm, wget, yum
  rpm : 리눅스 Redhat 계열에서 사용되는 명령어
        확장자가 .rpm 이어야하며 이를 패키지라고 부름
        윈도우의 setup.exe와 같은 유형
        미리 컴파일된 프로그램을 배포
          => i : 패키지 설치
             v : 설치과정 확인
             h : 설치진행과정을 #마크로 화면에 출력
             U : 패키지 업그레이드
             e : 패키지 삭제
             qa : 설치된 모든 패키지 확인
             qi : 설치된 패키지 정보 확인
             qpl : 패키지 파일에 어떤 파일이 포함되었는지 확인
             v : 패키지 검사
             a : 모든 패키지

  wget : 파일을 다운받는 명령어
         파일 주소를 알면 하드디스크에 저장 가능

  yum : 패키지 관리 프로그램
        rpm 명령어의 개선용 명령어
        파일이 있는 주소를 파일형태로 저장해 뒀다가 키워드만 입력하면 파일에서 찾아서 다운을 받는 형태
          => install : 설치
             check-update : 업데이트 가능한 목록 확인
             update : 패키지 업데이트
             remove : 패키지 삭제
             search : 인터넷에서 패키지 설치가 가능한지 확인
             info : 패키지 정보 학인
             list : 패키지 목록 확인
```

* ### **회고 (+,-,!)**
```
1. 뿌듯했던 점 (+)
    => (1) 오류가 발생했을 때 오류창을 해석하고 스스로 문제 해결 방법을 찾은 것
            -> recovery 명령어와 vim -r notice.txt 명령어 두가지 모두 시도해보았음 

       (2) 소유자와 그룹이 잘못되어 있다는 것을 발견해서 스스로 문제 해결
            -> 664 ss-univ를 root ss-univ 로 수정하기 위해 chown root.ss-univ board.txt 명령어를 입력
            -> 당황하지 않고 스스로 오류 해결

2. 보완할 점 (-)
    => 암기해야할 명령어들이 많음
      -> 억지로 외워야겠다는 생각보단 실습을 자주, 많이 해보며 자연스레 익히기

3. 꼭 기억할 점 (!) 
    => 파일의 공동 편집 및 관리 가능 but 그 허가 범위는 관리자가 지정할 수 있음
       누가 파일 or 디렉터리를 생성/관리할 수 있는 지
       해당 파일 or 디렉터리를 w(쓰고), r(읽고), x(실행)할 수 있는 지
```