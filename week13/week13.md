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
   
    [제로보드XE란 및 설치방법](https://blog.naver.com/anysecure3/220619174287)

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
    => 이번 주차는 새롭게 배운 워드프레스가 재미있게 느껴졌다. 지난 학기의 html/css 수업이 떠올라 낯설지 않았다. 워드프레스나 XE에 대해 공부해보니 html과 css로 힘들게 하드코딩하지 않아도 쉽고 빠르게 웹 페이지를 꾸밀 수 있음을 알게 되었다. 그래서인지 굳이 html과 css로 수작업을 해야할 필요가 있는 건가 하는 의문이 생기기도 하였다. 물론 웹 페이지 내부 구성을 알기 위해선 html과 css의 문법구조를 알아야하지만 단순히 웹 페이지를 제작하는 것이 목적이라면 워드프레스와 XE를 이용하는 방법이 훨씬 간단할 것 같다. 컴퓨터 시스템 관리 강의가 끝을 달리고 있는데 배우면 배울수록 점점 더 재밌어지는 것 같아 아쉽기도 하다. 앞으로 남은 주차의 실습도 오류로 힘들어하지 않고 재미있게 마무리할 수 있으면 좋겠다.<br>
       
2. ***보완할 점 (-)***
    => 강의에서 실습을 따라 진행할 땐 server에 워드프레스를 구축했기 때문에 server(b)에 과제를 진행할 땐 XE를 이용해보고 싶었다. 그러나 자꾸 오류도 발생하고 여러 게시물들에서 글로만 설명해주다보니까 어렵게 느껴졌다. 그래서 결국 server(b) 역시 워드프레스로 진행했는데 XE를 다루지 못한 점이 아쉬웠다. 이번 실습 과제를 하면서 워드프레스의 테마를 변경하는 작업을 진행해봤는데 기말고사 과제가 나오기 전에 다시 한번 워드프레스를 설치해 블로그 처럼 꾸며보고 싶다는 생각이 들었다. 기회가 된다면 XE로도 꼭 한번 작업해 보아야겠다.<br>
 
3. ***꼭 기억할 점 (!)*** 
    => 지난 수업들에서 배운 내용을 까먹지 않기, wget 명령어<br>
         -> wget이란 인터넷에서 파일을 받는 가장 좋은 방법으로 여러 복잡한 다운로드 상황을 거의 다 제어가능하다. <br>
         중간고사 이전의 수업에서 wget에 대하여 학습하였으나 더 알아보고자 한다.<br>
         $ wget DOWNLOAD-URL : 단일 파일 받기
         $ wget --limit-rate=200k DOWNLOAD-URL : 다운로드 속도 지정
         $ wget -c DOWNLOAD-URL : 이어받기
         $ wget --tries=75 DOWNLOAD-URL : 재시도 횟수 지정하기
         $ wget -i FILE-WHICH-HAS-URLS : 여러개의 파일 다운로드하기
         $ wget --mirror -p --convert-links -P ./LOCAL-DIR WEBSITE-URL : 전체 웹사이트 다운로드 받기
         $ wget --reject=gif WEBSITE-URL : 파일 타입에 따라 다운로드 제외
         $ wget -o download.log DOWNLOAD-URL : 로그파일 남기기
         $ wget -Q5m -i FILE-WHICH-HAS-URLS : 지정된 크기만큼만 다운로드
         $ wget -r -A.pdf WEBSITE-URL : 특정 파일 타입만 다운로드

    [wget 명령어를 사용해 리눅스 LAMP환경 구축](https://m.blog.naver.com/PostView.naver?blogId=cutecameron2&logNo=220543467221&proxyReferer=http:%2F%2F210.117.121.212%2F)

    [리눅스 wget 명령어 사용 예제](https://sisiblog.tistory.com/25F)