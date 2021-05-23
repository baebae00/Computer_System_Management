# 20200994 배서은
**컴퓨터시스템관리 12주차 실습일지**

---
#### 12주차에는 
1. 메일 서버와 관련된 용어와 작동방식 이해
2. 메일 서버 구축 및 기본 설정
---

## 1. 실습과제 결과

* ### **라운드 로빈 방식의 네임 서버 구현**
  
* #### **Server(b) 에 메일 서버를 추가로 구축하여, 이메일을 주고 받기** <br>
    
  * soo->peng, peng->soo 메일 주고받는 실습 영상
    <br>

    [이메일 주고받기 실습 영상](https://baedevelog.tistory.com/10)
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

- **SSH 접속 RSA 공유키 충돌오류**

    ![오류1](https://user-images.githubusercontent.com/77660379/119253652-2eb21c80-bbed-11eb-9033-0b50aa581982.JPG)

    ![오류1해결](https://user-images.githubusercontent.com/77660379/119253655-31ad0d00-bbed-11eb-8ec2-a3c69e5e274a.JPG)

    ```
    문제발생 및 고민한 내용 : SSH 접속 RSA 공유키 충돌오류

    해결 과정 : ssh@linux* 로 접속 시도
             -> '중간자 공격'에 대한 경고창 발생
             -> 이유는 같은 IP 로 기존에 접속한 적이 있는 서버와 RSA 공유키를 교환한 상태에서, 서버가 바뀌었기 때문
             -> 이 경우는 운영자인 내가 고의적으로 변경한 것이기에, 해킹 등의 침해사고는 아님(스푸핑 X)
             -> ssh-keygen -R* 명령어를 통해 초기화시켜 오류 해결
    ````
    [RSA 공유키 충돌오류 참고](https://cpuu.postype.com/post/30065)

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

  * /etc/bind/*.com.db에 사용된 코드 각각의 의미
   
   ![week11_참고할 만한 내용](https://user-images.githubusercontent.com/77660379/118093750-db7be500-b408-11eb-8edb-d382a4c7c556.JPG)
   
    [/etc/bind/*.com.db에 사용된 코드 의미](https://jerryk026.tistory.com/163)
   
    *$TTL*
    => Time to Live.*.com으로 호스트 이름을 질의 했을 떄, 다른 네임 서버가 해당 IP 주소를 캐시에 저장하는 시간을 뜻함

    *3H*
    => 3시간

    *@*
    => /etc/named.com에 정의된 john.com을 의미

    *SOA*
    => Start Of Authority. 권한의 시작, 괄호 안 숫자는 각각 버전 정보, 상위 네임 서버에 업데이트된 정보 요청하는 간격, 상위 네임 서버에 문제 발생 시 재접속 간격, 상위 네임 서버에 접속 불가시 이전 정보 파기 간격, 이 시간 이후에 정보가 삭제되는 데 걸리는 시간을 뜻함

   *NS*
    => Name Server 설정된 도메인의 네임 서버 역할을 하는 컴퓨터를 지정함

    *MX*
    => Mail Exchange. 메일 서버 컴퓨터를 설정

    *A*
    => 호스트 이름에 상응하는 IP 주소를 지정
    
    *CNAME*
    => 호스트 이름에 별칭을 부여할 때 사용

* ### **회고 (+,-,!)**

1. *뿌듯했던 점 (+)*
    => 라운드 로빈 방식의 네임 서버 구현에 흥미를 느낀 것
          -> 작년 웹페이지를 제작하는 수업이 정말 재미있었다. 내가 만든 웹 페이지가 .~.com으로 접속 가능하다는 것이 신기했기 때문이다. 이번 11주차 실습에서도 이와 같은 흥미를 느꼈는데 웹 페이지를 직접 만들진 않았지만 IP주소로 웹 서버에 접속 할 수 있다는 방식이 유익했다. 컴퓨터는 배우면 배울수록 복잡해질수록 더욱 더 신기하고 재미있어지는 것 같다.<br>
       
2. *보완할 점 (-)*
    => 실습은 한번에 끝내기
      -> 이번 실습에서 server 백업을 5번 정도 진행했다. 강의를 다 듣고 나서 과제를 하던 중에 일이 생겨서 또 몇시간 뒤에 다시 진행하니 RSA 공유키 충돌 문제가 발생하고 다시 백업하고 이를 몇번이고 반복했다. 이번 실습이 어렵진 않았지만 한번에 실습을 끝내지 않는 걸 자꾸 반복하다보니 오류가 생겨 해결하는데만 오랜 시간을 써버렸다. 실습은 한번에 마무리해야 된다는 것을 깨달았다. <br>
 
3. *꼭 기억할 점 (!)* 
    => 변경 사항 저장
         -> 라운드 로빈 방식의 웹 서버를 구현할 떄에는 항상 systemctl restart * 과정을 진행해야한다. 변경 사항을 저장하기 위해 systemctl restart named를 입력하고 네임 서버를 다시 가동한 후 nslookup 명령어를 입력해 server IP를 통헤 서버 정보를 확인할 수 있다.