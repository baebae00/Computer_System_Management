# 20200994 배서은
**컴퓨터시스템관리 13주차 실습일지**

---
#### 13주차에는 
1. 웹 서버와 관련된 용어와 작동방식 이해
2. 웹 서버 구현 및 관련 파일 편집
3. 웹 서버를 이용한 간단한 웹 사이트 구축
---

## 1. 실습과제 결과

* ### **웹 서버 구축 후 웹 페이지 제작 실습**
  
* #### **Server(b) 에 웹 서버 구축한 뒤, 웹 페이지 만들기** <br>
    
  * Server(b) 에 wordpress를 구축해 웹 페이지를 만든다.
    <br>

    [wordpress 웹 페이지 제작 실습 영상](https://baedevelog.tistory.com/10)
    <br>
     
     ![실습결과](https://user-images.githubusercontent.com/77660379/119253310-94050e00-bbeb-11eb-945b-3473cbdf781d.JPG)
    <br><br>

## 2. 실습과제 Review

* ### **새로 배운 내용**

```
1. Mail Server(SMTP, POP3, IMAP)
    => Email 의 송수신에서 사용되는 프로토콜
       -> SMTP, Simple Mail Transfer Protocol
          클라이언트가 메일을 보내거나, 메일 서버끼리 메일을 주고 받을 때
       POP3, Post Office Protocol
       -> 메일 서버에 도착되어 있는 메일을 클라이언트로 가져올 때(서버에서 로컬 장치로 다운로드)
       -> IMAP, Internet Mail Access Protocol
          POP3 와 유사, 중앙 서버에서 동기화
          모든 장치에서 동인한 이메일 확인 가능

2. Sendmail
    => 인터넷에서 메일을 전송하기 위해 사용되는 패키지
       MTA, Mail Transfer Agent
       SMTP, Simple Mail Transport Protocol
        -> 25번 포트 사용
       주요 설정 파일
        -> /user/bin/sendmail : 데몬 파일
        -> /user/bin/makemap : 맵 생성 실헹파일
        -> /var/spool/mqueue : 메일을 일시 저장하는 디렉터리
        -> /var/spool/mail : 개별 메일을 보관하는 디렉터리
        -> /etc/mail/access : relay 제한 및 설정 파일 (스팸 메일 방지 등)
            RELAY : 관련 메일 수신/발신 허용
            REJECT : 관련 메일 수신/발신 거부
        -> /etc/mail/sendmail.cf : sendmail 설정 파일
```

* ### **문제가 발생하거나 고민한 내용 + 해결 과정**

- **워드프레스 HTTP error 500 오류**

    ![오류1](https://user-images.githubusercontent.com/77660379/119448473-5a0f4580-bd6c-11eb-85b0-1f17e7cee39f.JPG)

    ![오류1시도1](https://user-images.githubusercontent.com/77660379/119448479-5c719f80-bd6c-11eb-8f51-82abb7ee4194.JPG)

    ![오류1시도2](https://user-images.githubusercontent.com/77660379/119448481-5d0a3600-bd6c-11eb-9bbb-b5b7999461d8.JPG)

    ![오류1해결1](https://user-images.githubusercontent.com/77660379/119448482-5d0a3600-bd6c-11eb-89ae-1d3affce4421.JPG)

    ![오류1해결2](https://user-images.githubusercontent.com/77660379/119448483-5da2cc80-bd6c-11eb-8c82-30109540064b.JPG)

    ![오류1해결완료](https://user-images.githubusercontent.com/77660379/119448485-5e3b6300-bd6c-11eb-8def-63d45cf905d5.JPG)

    ```
    문제발생 및 고민한 내용 : SSH 접속 RSA 공유키 충돌오류

    해결 과정 : ssh@linux* 로 접속 시도
             -> '중간자 공격'에 대한 경고창 발생
             -> 이유는 같은 IP 로 기존에 접속한 적이 있는 서버와 RSA 공유키를 교환한 상태에서, 서버가 바뀌었기 때문
             -> 이 경우는 운영자인 내가 고의적으로 변경한 것이기에, 해킹 등의 침해사고는 아님(스푸핑 X)
             -> ssh-keygen -R* 명령어를 통해 초기화시켜 오류 해결
    ````
    [Ubuntu 방화벽 작동상태 참고](http://blog.plura.io/?p=4580)

    [500 내부 서버 오류 참고](https://kor.go-travels.com/34459-500-internal-server-error-explained-2622938-8098952)

    [HTTP 500 내부 서버 오류 생성 참고](https://www.psychz.net/client/question/ko/http-500-internal-server-error.html2)

    [워드프레스 HTTP error 500 문제 해결 참고](https://congjang.com/entry/%EC%9B%8C%EB%93%9C%ED%94%84%EB%A0%88%EC%8A%A4-HTTP-error-500%EB%AC%B8%EC%A0%9C-%ED%95%B4%EA%B2%B0)

- **E212: Can't open file for writing 오류**

    ![오류2](https://user-images.githubusercontent.com/77660379/119253735-8f415980-bbed-11eb-8eca-e9b4353cb815.JPG)

    ```
    문제발생 및 고민한 내용 : E212: Can't open file for writing 오류

    해결 과정 : vi 파일 저장 및 종료 시도
               -> E212 오류 발생
               -> 기본적으로 권한이 없는 곳에서 파일을 만들거나 수정할 때 생기는 문제
               -> :q! 로 강제 종료 후 다시 작성할 수 있으나 이런 경우가 때때로 발생하기 때문에 해결 방법을 찾으려함
               -> :w !sudo tee % > /dev/null 명령어를 통해 오류 해결 후 vi 파일 저장 및 종료
    ````
    [E212: Can't open file for writing 오류 참고](https://noosphere.tistory.com/81)


* ### **참고할 만한 내용**

  * mail 전송의 원리
   
   ![메일전송의원리](https://user-images.githubusercontent.com/77660379/119254313-93bb4180-bbf0-11eb-90c7-28e2e45fc3a7.JPG)
   
    [mail 전송의 원리](https://unabated.tistory.com/entry/mail-%EC%A0%84%EC%86%A1%EC%9D%98-%EC%9B%90%EB%A6%AC)
   
    *MUA(Mail User Agent)*
    => 메일을 작성하여 보내는 프로그램

    *MTA(Mail Transfer Agent)*
    => 이용자로부터 메일을 받아서, 외부로 전달하는 프로그램

    *MDA(Mail Delivery Agent)*
    => 전송받은 메일을 해당 사용자에게 전달

    *메일 전송의 원리*
    => 사용자는 mail client와 같은 프로그램을 통해 mail 작성 후 , SMTP를 사용해 mail deamon으로 메시지 전송
       -> mail deamon은 client의 주소를 분석하고 가장 가까운 mail server로 메시지와 정보를 보냄
       -> 송신자가 보낸 편지가 송신자 측의 전자우편을 관리하는 mail server에 전달되면, mail server는 수신자의 전자우편 주소를 분석해 최단 경로를 찾아 근접한 mail server에 편지를 전달
       -> 최종 수신자측의 mail server에 도착하기까지 연속적으로 전달하는 중계작업이 계속됨
       -> 이러한 일련의 작업이 계속적으로 이루어진 후, 송수신자는 정확하게 메일 교환이 가능해짐

   *MUA&MTA*
    => 사용자가 직접 접하게 되는 것은 우편 대행자(MUAL: Mail User Agent)
       이 메일은 크게 두가지로 발전
        -> BSD(Berkely Software Distribution)에서 개발된 mailx
        -> System V Unix에서 개발된 Mail

* ### **회고 (+,-,!)**

1. *뿌듯했던 점 (+)*
    => vi .swap파일 오류 발생 해결
          -> 지금까지 vi로 만든 파일의 내용을 수정하면서 오류가 생기면 쉽게 해결이 안돼서 서버를 초기화한 후 처음부터 다시 진행하기 바빴다. 하지만 이번 실습을 진행하면서 vi로 만든 파일에 오류가 생겨 *.swap 파일이 추가로 생성되었을 때 :recover 명령어 > Enter로 해결가능하다는 사실을 새롭게 알게 되었다. 항상 오류가 발생할 때마다 괴로워하며 초기화와 재생성을 반복했는데 간단한 명령어로 쉽게 오류를 해결할 수 있음을 깨닫고 나니 뿌듯했다. 어느 과정에서든 오류가 발생했을 땐 항상 오류 문구와 해결 방안 문구를 천천히 살펴봐야한다는 점을 이번 실습에서도 느꼈다.<br>
       
2. *보완할 점 (-)*
    => DNS server와 mail server 구분 및 vi 파일 작성
      -> Server(b)에 메일 서버를 구축할 때 /etc/bind/it.ac.kr.db, /etc/resolv.conf, /etc/hosts 각각의 파일에 서버 주소를 작성하는 과정이 헷갈렸다. 강의를 따라가며 실습할 때는 문제가 없었지만 Server(b)에 따로 메일 서버를 추가로 구축하려 실습을 하다보니 어느 파일에 Server의 주소를 작성해야하는 건지, 또 어떤 파일에 Sever(b)의 주소를 작성해야하는 건지 복잡했기 때문이다. mail server의 작동원리를 정리해보면서 실습을 한번 더 진행해보면 이 부분은 보완될 것 같다. 다음으로 vi 파일에 내용을 작성하고 오타가 발생하면 지우고 하는 과정은 아직도 어려운 것 같다. backspace로 지우고 싶은데 del 버튼으로만 삭제 가능하고 insert모드로 변경했는데 문자가 작성되지 않는 오류가 종종 발생하기 때문이다. vi로 만든 파일을 다룰 때는 최대한 오타 없이 내용을 작성해야 되겠다.<br>
 
3. *꼭 기억할 점 (!)* 
    => mutt을 이용하면 파일을 첨부한 메일 전송 가능 <br>
         -> 실습일지를 작성하면서 리눅스 mail송수신에 대해 더 알아보다가 흥미로운 사실을 발견했다. mutt을 이용하면 파일을 첨부한 메일을 보낼 수 있다는 점이다.
         $ yum -y install mutt 명령어를 통해 yum을 설치해준다. 이후 <br>
         $ mutt -s "메일제목" 메일주소 < 본문내용파일 -a 첨부파일명 명령어를 실행하게 되면 파일이 첨부되어 메일이 보내진다. <br>
         추가적으로 -c옵선을 사용하면 cc 즉 참조로 받을 메일 주소를 더 넣을 수 있고 -b 옵션은 숨은 참조를 지정하는 옵션이다. <br> 여러 명에게 메일을 전송할 때는 메일 주소 뒤에 메일 주소를 추가로 넣어주면 된다.

    [mutt을 이용한 파일첨부 메일 전송](http://blog.naver.com/PostView.nhn?blogId=mrkaze&logNo=220989047552)