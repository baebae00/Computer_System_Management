# 20200994 배서은
**컴퓨터시스템관리 14주차 실습일지**

---
#### 14주차에는 
1. 방화벽 서버와 관련된 용어와 작동방식 이해
2. 방화벽 서버 구현 및 관련 파일 편집
---

## 1. 실습과제 결과

* ### **방화벽 컴퓨터를 구축한 후 Server(b)에 웹 서버 구축 및 wordpress를 설치해 Host Computer에서 접속 실습**
  
* #### **Host Computer에서 192.168.56.131 ip 주소로 접속** <br>

    [Host Computer에서 192.168.56.131 ip 주소로 접속 실습 영상](https://baedevelog.tistory.com/12)
    <br><br>

     *Server(b)*
     ![serber(b)](https://user-images.githubusercontent.com/77660379/120380549-465f7280-c35c-11eb-9198-cc021e5ca84e.JPG)

    <br>*Client*

     ![client](https://user-images.githubusercontent.com/77660379/120380563-49f2f980-c35c-11eb-909d-7d27da10186a.JPG)

     <br>*Server*

     ![server](https://user-images.githubusercontent.com/77660379/120380570-4bbcbd00-c35c-11eb-88b9-d7b390237696.JPG)

     <br>*wordpress*
     ![웹서버](https://user-images.githubusercontent.com/77660379/120380575-4d868080-c35c-11eb-9e4f-4507dbad418d.JPG)
    <br><br>

## 2. 실습과제 Review

* ### **새로 배운 내용**

1. 방화벽 Firewall
    => 미리 정의된 보안 규칙에 기반하여, 들어오고 나가는 네트워크 트래픽을 모니터링하고 제어하는 네트워크 보안 시스템<br>
       신뢰할 수 있는 내부 네트워크와 신뢰할 수 없는 외부 네트워크간의 장벽 구성<br>
       -> 정책 기반 방화벽<br>
            모두 차단 또는 모두 허용<br>
            특정 서버에서 오는 얼마 이상의 http 트래픽을 허용하고 <br>로그 남기기<br>
       -> 구현 방법에 따른 방화뱍 분류<br>
            SW 방화벽<br>
            HW 방화벽 : 초당 패킷 처리 수 증가<br>
            NPU 기반 방화벽 : SW+HW 방화벽<br>
       -> nonroutable IP 주소를 활용한 네트워크 구성<br>
            사설 IP를 이용하여 내부 컴퓨터 상이이 트래픽은 허용하고, 외부 인터넷과의 접속은 허용 또는 제한하는 방법<br>
            사설 IP 범위에 있는 컴퓨터는 인터넷 라우터를 통과할 수 없으나 설정(IP 마스커레이딩 등)을 통해 외부 인터넷 접속 가능<br>
       -> IP 마스커레이딩 IP Masquerading<br>
            masquerade, 진실 진심을 숨기는 가장(가식), 가장 무도회
            내부 컴퓨터들이 리눅스 서버를 통해 인터넷 등 다른 네트워크에 접속할 수 있게 해주는 기능<br>
            리눅스의 NAT(Network Address Translation) 기능 : IP 패킷의 TCP/UDP 포트 숫자와 소스 및 목적지의 IP 주소 등을 재기록 하면서 라우터를 통해 네트워크 트래픽을 <br>주고받는 기술, 주로 사설 네트워크에 속한 여러 개의 호스트가 하나의 공인 IP 주소를 사용하여 인터넷에 접속하기 위해 사용됨
       -> 방화벽 정책<br>
            내부 컴퓨터는 외부 인터넷을 사용할 수 있도록 한다.<br>
            외부 컴퓨터는 내부에 접속할 수 없도록 한다.<br>
            외부 컴퓨터가 방화젹 서버의 공인 IP로 웹 서비스를 요철할 때는 내부에 있는 웹 서버가 서비스 한다.<br>

2. iptables
    => 시스템 관리자가 리눅스 커널 방화벽이 제공하는 테이블과 그것을 저장하는 체인, 규칙들을 구성할 수 있게 해주는 사용자 공간 응용 프로그램

    [리눅스 서버에 방화벽을 활용하여 특정 IP만 접근하게 하는 방법 참고](https://uxgjs.tistory.com/162)

    [리눅스 방화벽 상태 확인 by 명령어 실행 파악 참고](https://jootc.com/p/201808031482)

    [iptables 개념 및 명령어 참고](https://linuxstory1.tistory.com/entry/iptables-%EA%B8%B0%EB%B3%B8-%EB%AA%85%EB%A0%B9%EC%96%B4-%EB%B0%8F-%EC%98%B5%EC%85%98-%EB%AA%85%EB%A0%B9%EC%96%B4)

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