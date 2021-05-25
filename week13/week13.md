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

    [wordpress 웹 페이지 제작 실습 영상](https://baedevelog.tistory.com/11)
    <br>
     
     *웹 브라우저에서 워드프레스 설치 및 워드프레스 관리자 설정*<br>

     ![1](https://user-images.githubusercontent.com/77660379/119457747-f9d1d100-bd76-11eb-8e80-94cb8f2de5d7.JPG)

     ![2](https://user-images.githubusercontent.com/77660379/119457751-fb02fe00-bd76-11eb-9735-462b37b0627f.JPG)

     ![3](https://user-images.githubusercontent.com/77660379/119458306-9005f700-bd77-11eb-92e3-cdd7868735d8.JPG)

    <br><br>

## 2. 실습과제 Review

* ### **새로 배운 내용**

1. 웹 서버
    => 웹 브라우저와 같은 클라이언트로 부터 HTTP 요청을 받아들이고, HTML 문서와 같은 웹 페이지를 반환하는 컴퓨터 프로그램
       위와 같은 기능을 제공하는 컴퓨터 프로그램을 실행하는 컴퓨터
       -> 아파치 Apache
          오픈소스 HTTP Server
          MPM(Multi Processing Module) 아키텍쳐 기반
          클라이언트의 요청을 스레드 형태의 서버 프로세스로 생성하여 처리
          1995년, 월드와이드웹 서버용 소프트웨어로 발표
          1999년, 아파치소프트웨어 재단에서 지원

2. LAMP
    => Linux + Apache + MySQL + PHP
       -> Apache HTTP Server
          HTTP 웹 서버
       -> MySQL
          관계형 데이터베이스 관리 시스템
       -> PHP(PHP: Hypertext Preprocessor)
          동적 웹 페이지를 만들기 위해 설계된 PL

* ### **문제가 발생하거나 고민한 내용 + 해결 과정**

- **워드프레스 HTTP error 500 오류**

    ![오류1](https://user-images.githubusercontent.com/77660379/119448473-5a0f4580-bd6c-11eb-85b0-1f17e7cee39f.JPG)

    ![오류1시도1](https://user-images.githubusercontent.com/77660379/119448479-5c719f80-bd6c-11eb-8f51-82abb7ee4194.JPG)

    ![오류1시도2](https://user-images.githubusercontent.com/77660379/119448481-5d0a3600-bd6c-11eb-9bbb-b5b7999461d8.JPG)

    ![오류1해결1](https://user-images.githubusercontent.com/77660379/119448482-5d0a3600-bd6c-11eb-89ae-1d3affce4421.JPG)

    ![오류1해결2](https://user-images.githubusercontent.com/77660379/119448483-5da2cc80-bd6c-11eb-8c82-30109540064b.JPG)

    ![오류1해결완료](https://user-images.githubusercontent.com/77660379/119448485-5e3b6300-bd6c-11eb-8def-63d45cf905d5.JPG)

    <br>

    ***문제발생 및 고민한 내용*** : 워드프레스 HTTP error 500 오류

    ***해결 과정*** : 호스트 컴퓨터로 192.168.56.131 서버 접속 시도<br>
             -> '페이지가 작동하지 않습니다. 현재 192.168.56.131에서 요청한 처리를 할 수 없습니다. HTTP ERROR 500' 이라는 오류창 발생<br>
             -> ping을 날려 연결 확인을 해본 결과 문제 없음<br>
             -> 방화벽 확인했으나 문제 없음<br>
             -> 이유는 php파일 중 하나의 소스에 문제가 있었기 때문<br>
             -> 워드프레스 설정 파일 (wp-config.php)의 변경사항이 저장되어 있지 않았음<br>
             -> wp-config.php파일의 23, 26, 29행의 변경사항을 수정 및 저장해 오류 해결
    
    [Ubuntu 방화벽 작동상태 참고](http://blog.plura.io/?p=4580)

    [500 내부 서버 오류 참고](https://kor.go-travels.com/34459-500-internal-server-error-explained-2622938-8098952)

    [HTTP 500 내부 서버 오류 생성 참고](https://www.psychz.net/client/question/ko/http-500-internal-server-error.html2)

    [워드프레스 HTTP error 500 문제 해결 참고](https://congjang.com/entry/%EC%9B%8C%EB%93%9C%ED%94%84%EB%A0%88%EC%8A%A4-HTTP-error-500%EB%AC%B8%EC%A0%9C-%ED%95%B4%EA%B2%B0)

* ### **참고할 만한 내용**

  * 제로보드XE
   
    [제로보드XE](https://blog.naver.com/anysecure3/220619174287)

    *Xpress Engine 제로보드*
    => 보다 쉽고 편하게 컨텐츠를 작성하고 관리할 수 있는 컨텐츠 관리 시스템(CMS) <br>
    'NHN' 에 인수되어 지원을 받고 있으며 명칭은 '제로보드xe' 혹은 Express Engine(XE)라고 부르고있음
      -> 홈페이지 계정 내에 설치하는 설치형 게시판
         홈페이지용 전자게시판 소프트웨어 또는 프로임워크로 PHP라는 언어로 쓰여짐
         PHP(Personal Hypertext Preprocessor)
          -> 하이퍼텍스트 생선언어에 포함되어 동작하는 스크립팅 언어
         HTML(HyperText Markup Language)
          -> 하이퍼텍스트를 작성하기 위해 개발된 웹 문서를 만들기 위한 기본적인 프로그래밍 언어의 한 종류

* ### **회고 (+,-,!)**

1. ***뿌듯했던 점 (+)***
    => vi .swap파일 오류 발생 해결
          -> 지금까지 vi로 만든 파일의 내용을 수정하면서 오류가 생기면 쉽게 해결이 안돼서 서버를 초기화한 후 처음부터 다시 진행하기 바빴다. 하지만 이번 실습을 진행하면서 vi로 만든 파일에 오류가 생겨 *.swap 파일이 추가로 생성되었을 때 :recover 명령어 > Enter로 해결가능하다는 사실을 새롭게 알게 되었다. 항상 오류가 발생할 때마다 괴로워하며 초기화와 재생성을 반복했는데 간단한 명령어로 쉽게 오류를 해결할 수 있음을 깨닫고 나니 뿌듯했다. 어느 과정에서든 오류가 발생했을 땐 항상 오류 문구와 해결 방안 문구를 천천히 살펴봐야한다는 점을 이번 실습에서도 느꼈다.<br>
       
2. ***보완할 점 (-)***
    => DNS server와 mail server 구분 및 vi 파일 작성
      -> Server(b)에 메일 서버를 구축할 때 /etc/bind/it.ac.kr.db, /etc/resolv.conf, /etc/hosts 각각의 파일에 서버 주소를 작성하는 과정이 헷갈렸다. 강의를 따라가며 실습할 때는 문제가 없었지만 Server(b)에 따로 메일 서버를 추가로 구축하려 실습을 하다보니 어느 파일에 Server의 주소를 작성해야하는 건지, 또 어떤 파일에 Sever(b)의 주소를 작성해야하는 건지 복잡했기 때문이다. mail server의 작동원리를 정리해보면서 실습을 한번 더 진행해보면 이 부분은 보완될 것 같다. 다음으로 vi 파일에 내용을 작성하고 오타가 발생하면 지우고 하는 과정은 아직도 어려운 것 같다. backspace로 지우고 싶은데 del 버튼으로만 삭제 가능하고 insert모드로 변경했는데 문자가 작성되지 않는 오류가 종종 발생하기 때문이다. vi로 만든 파일을 다룰 때는 최대한 오타 없이 내용을 작성해야 되겠다.<br>
 
3. ***꼭 기억할 점 (!)*** 
    => mutt을 이용하면 파일을 첨부한 메일 전송 가능 <br>
         -> 실습일지를 작성하면서 리눅스 mail송수신에 대해 더 알아보다가 흥미로운 사실을 발견했다. mutt을 이용하면 파일을 첨부한 메일을 보낼 수 있다는 점이다.
         $ yum -y install mutt 명령어를 통해 yum을 설치해준다. 이후 <br>
         $ mutt -s "메일제목" 메일주소 < 본문내용파일 -a 첨부파일명 명령어를 실행하게 되면 파일이 첨부되어 메일이 보내진다. <br>
         추가적으로 -c옵선을 사용하면 cc 즉 참조로 받을 메일 주소를 더 넣을 수 있고 -b 옵션은 숨은 참조를 지정하는 옵션이다. <br> 여러 명에게 메일을 전송할 때는 메일 주소 뒤에 메일 주소를 추가로 넣어주면 된다.

    [mutt을 이용한 파일첨부 메일 전송](http://blog.naver.com/PostView.nhn?blogId=mrkaze&logNo=220989047552)