# 20200994 배서은
**컴퓨터시스템관리 2주차 실습일지**

---
#### 2주차에는 
1. 컴퓨터 시스템의 기본 구조와 운영체제의 역할 이해
2. 리눅스가 설치된 컴퓨터를 사용하기 위한 기본 방법 이해
3. 시스템 관리자로서 기본적인 리눅스 명령어를 실습
---

## 1. 실습과제 결과

* ### **리눅스 기본 명령어 중 잘 모르는 3개를 선정 후 각각의 man 페이지를 OO_man.txt 파일로 저장한 뒤, 자신의 학번으로 압축**
  
  **CHECK POINT** <br>
  *vmware 가상환경의 firefox웹사이트를 이용하면 실제 pc 환경과 연동시키지 않아도 파일을 업로드 할 수 있다*

* ### **man.txt파일 -> tar.gz압축** <br>
    [20200994.tar.gz URL](https://baedevelog.tistory.com/6)

  - man less

    ![man less](https://user-images.githubusercontent.com/77660379/111018670-7f431780-83fd-11eb-87c3-12e49cba1e32.JPG)
  
  - man more
      
    ![man more](https://user-images.githubusercontent.com/77660379/111018706-b9141e00-83fd-11eb-9074-36379f4c51c2.JPG)
  
  - man mount
      
    ![man mount](https://user-images.githubusercontent.com/77660379/111018710-c7fad080-83fd-11eb-9f2a-88cbacf43d7c.JPG)

* ### **실습 과정**
  - test 내 파일 삭제

    ![test 내 파일 삭제](https://user-images.githubusercontent.com/77660379/111018888-296f6f00-83ff-11eb-8363-16113050ea85.JPG)

    ```
    실습 강의를 보고 따라하는 과정에서 생성한 test 내 여러 파일들과 압축 파일들을 전부 제거하였다.
    한번에 여러가지의 파일을 삭제하고 싶을 땐 
    -> rm -r test1.txt test2.txt 와 같이 
    rm -r * (* 자리에 제거할 파일명을 나열) 의 방법을 사용하면 보다 편리하다는 사실을 새롭게 알게 되었다.
    ```
  - test > OO_man.txt 파일 3개 생성

    ![00_man txt 파일 생성](https://user-images.githubusercontent.com/77660379/111018922-59b70d80-83ff-11eb-827f-f2a5b986ad14.JPG)


    ```
    1) touch less_man.txt (.txt파일 생성) => man less > less_man.txt (less에 대한 man 페이지를 less_man.txt 파일에 저장)
    2) touch more_man.txt => man more > more_man.txt (more에 대한 man 페이지를 more_man.txt 파일에 저장)
    3) touch mount_man.txt => man mount > mount_man.txt (mount에 대한 man 페이지를 mount_man.txt 파일에 저장)
    ```
  - tar 파일로 묶고, gzip 으로 압축

    ![압축](https://user-images.githubusercontent.com/77660379/111018936-6c314700-83ff-11eb-8d8a-4ee9af6180e0.JPG)


    ```
    상위 디렉토리로 이동하여 test에 접근하였다.
    (test 내에 less_man.txt, more_man.txt, mount_man.txt 파일이 존재하기 때문)
    터미널 창에 명령어는 tar zcvf gzip.tar.gz test 를 이용하였다.
    
    파일 압축 방법에는 2가지가 있는데,
    1) gzip 으로 압축할 경우 : tar zcvf gzip.tar.gz *
    2) bzip2 로 압축할 경우 : tar jcvf bzip2.tar.bz2 *
    의 명령어를 사용하면 된다.
    ```
  - TISTORY에 tar.gz 업로드

    ![firefox로 업로드](https://user-images.githubusercontent.com/77660379/111018954-7ce1bd00-83ff-11eb-8dbb-19919a4a6f43.JPG)

    ```
    vmware 가상 환경 내 firefox 웹 사이트로 tistory에 접근하였다.
    파일 첨부 과정은 drag-and-drop 으로 가능했고,
    실제 PC와 가상환경 내의 압축 폴더를 연동시키지 않아도 업로드 가능하다는 점에서 편리했다.
    ```

## 2. 실습과제 Review
* ### **새로 배운 내용**
```
1. 커널 Kernel
    => 커널 모드에서 동작하는, OS의 핵심부분이 되는 처리를 모아 담당하는 프로그램
       커널 모드에서 처리하는 것
       -> 프로세스 관리 시스템, 프로세스 스케줄링, 메모리 관리 시스템

2. 명령어 도움말 man (manual pages)
    => 유닉스 및 유닉스 계열 운영체제에 기본으로 설치되어 있는 문서
       man <명령어_이름>
       man ls
       행 이동 방법 : 화살표 위 / 아래, 또는 K / J
       페이지 단위 이동 방법 : PageUp / PageDown 또는 Space bar / B
       특정 단어 검색 : /단어
        -> 다음 단어로 이동시 N, 종료는 Q

3. vi 에디터 명령어
     => man ls > man_ls.txt : ls의 man페이지를 man_ls.txt 파일에 저장
        rm -rf <파일명> : 파일 삭제
        vi test.py : python 파일 생성
        cd test : test로 이동
        cd .. : 상위 디렉토리로 이동
        mkdir test : test 디렉토리 생성
        cp : 파일 복사
        pwd : 현재 디렉토리의 위치 출력
        touch test.txt : test.txt 파일 생성
        more : 터미널 창 크기에 맞춰서 파일 출력
        less : more 와 유사하지만 상위호환
        clear : 터미널 내용 지우기
        cat : 파일 만들기
        file : 파일의 종류를 출력


4. 마운트 mount
     => 리눅스에서는 모든 장치를 파일 형태로 다룸 (파일시스템)
        하드디스크의 파티션, CD/DVD, USB 메모리 등을 사용하려면 지정한 위치에 연결해야함
        물리적 장치를 특정한 위치에 연결하는 과정이 '마운트'

5. 파일 묶기와 압축
     => 데이터 압축
            -> 데이터를 더 적은 공간에 효율적으로 기록하기 위한 기술
               윈도우에서 '파일을 압축한다' 라는 것은 '파일을 (묶고) 압축한다' 라는 것과 동일
               리눅스에서는 파일을 묶고, 압축해야함
        tar
            -> Tape ARchive
               tar 로 묶여지기 전 파일들의 속성, 심볼릭 링크, 디렉토리 구조 등을 그대로 가져갈 수 있음 
```

* ### **문제가 발생하거나 고민한 내용 + 해결 과정**
```
1. 문제발생 및 고민한 내용
  압축 폴더 업로드
    => Why? tar.gz 폴더는 vmware 가상환경 상에 생성한 폴더이기 때문에 이를 실제 PC와 연동해 업로드하는 방법이 무엇일지 고민함

2. 해결 과정
  실제 PC의 폴더 내에 압축한 tar.gz 폴더가 존재하는 지 찾아봄
  (1) 가상환경에서 생성한 폴더이기 때문에 실제 PC에 존재할 리 없음
  (2) 구글링을 통해 호스트와 가상머신간 같은 폴더를 공유하는 방법을 알아냄
    (a) 공유할 가상 머신의 세팅 > 옵션 
    (b) hared Folders 항목 추가
    (c) Always enabled로 바꾸고 Map as a network drive in Windows guests 항목 체크
    (d) 공유 폴더 지정을 위해 추가 버튼 클릭
    (e) 공유할 호스트의 폴더 지정
    (f) Name은 20200994로 지정
    (g) 공유 권한을 물으면 Enabled this share 항목 체크
  (3) 이렇게 하면 가상머신에서 공유 파일 지정은 끝이 남
  (4) 그러나 너무 복잡해서 다른 방법은 없을까 고민
  (5) Slack #qna 창의 질문-답변을 참고하여 가상환경에서 바로 파일을 업로드하는 방법이 있다는 사실을 알게됨
  (6) vmware 내 firefox 웹사이트로 파일을 업로드할 주소인 tistory에 접근
  (7) 정보의 공유에 대한 중요성을 깨달음 qna 덕분에 보다 쉽게 파일 업로드 가능해짐
```

* ### **참고할 만한 내용**
```
런레벨 변경하기
  => Server부팅 및 터미널 열기
  => 설정된 런레벨 확인
    : ls -l /lib/systemd/system/default.target
  => 런레벨 변경 (그래픽 모드 -> 텍스트 모드)
    : ln -sf /lib/systemd/system/multi-user.target / lib/systemd/system/default.target
      ls -l /lib/systemd/system/default.target
      reboot
  => X윈도우 실행
    : startx
  => 런레벨 변경 (텍스트 모드 -> 그래픽 모드)
    : ln -sf /lib/systemd/system/graphical.target /lib/systemd/system/default.target
     reboot

런레벨의 변경은 root 사용자만 가능, 터미널 명령어로 변경할 수도 있고 gedit을 통해서 수정해 줄 수도 있음
```

* ### **회고 (+,-,!)**
```
1. 뿌듯했던 점 (+)
    => (1) github 사용이 능숙해짐 issues에 이미지를 등록하고 vscode를 통해 커밋하는 것이 더이상 어렵지 않음
       (2) 잘 모르겠는 명령어들은 강의를 3번씩 반복해가며 들으며 이해한 것
       (3) 한번에 여러개의 파일을 한꺼번에 제거하는 방법을 스스로 습득한 것

2. 보완할 점 (-)
    => Slack의 #qna 창을 적극적으로 활용하기
      -> 호스트와 가상머신간 폴더를 공유하도록 환경을 설정하는 방법보다 더 나은 대안이 있다는 사실을 qna 창을 통해 미리 알았더라면 실습을 보다 빠르게 끝낼 수 있었을 것임
      -> 다른 학생들의 질문과 답변을 참고하며 함께 배우려는 자세를 갖춰야할 필요가 있음 (이미 알고있는 사실이더라도 한번 더 공부하는 자세)

3. 꼭 기억할 점 (!) 
    => 가상환경에서도 인터넷에 접근 가능, 가상환경 역시 실제 PC와 같은 기능을 갖추고 있음
```