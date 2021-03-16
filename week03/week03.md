# 20200994 배서은
**컴퓨터시스템관리 3주차 실습일지**

---
#### 3주차에는 
1. 리눅스 파일시스템의 기본 디렉터리 구조 이해
2. 리눅스가 설치된 컴퓨터를 사용하기 위한 기본 방법 이해
3. 시스템 관리자로서 기본적인 리눅스 명령어 실습 
---

## 1. 실습과제 결과

* ### **리눅스 프로그램 설치, 소개 및 동작 화면 캡쳐**
  
  **CHECK POINT** <br>
  *검색엔진에 '리눅스 커맨드라인 툴' or 'linux command line tools'를 검색하여 설치할 패키지명과 방법을 알 수 있다*

* ### **Installation of Lolcat in Linux** <br>
    
    ```
    Lolcat은 리눅스, BSD, OSX용 유틸리티로 캣 명령과 유사하게 연결되며 무지개 색을 추가하는 패키지
    리눅스 터미널에서 텍스트의 무지개 색상에 주로 사용됨
    ```

  - apt-get install ruby

    ![install ruby](https://user-images.githubusercontent.com/77660379/111276033-3c41a800-867a-11eb-9353-6ee0228e1e55.JPG)

* ### **Usage of Lolcat**
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