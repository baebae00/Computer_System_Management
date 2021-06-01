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

- **FireFox > google.co.kr 접속 오류**

    ![오류1](https://user-images.githubusercontent.com/77660379/120382641-d7cfe400-c35e-11eb-87b7-cf3f66ba8465.JPG)

    ![오류1해결](https://user-images.githubusercontent.com/77660379/120382645-db636b00-c35e-11eb-882d-ad8056738524.JPG)

    ***문제발생 및 고민한 내용*** : FireFox > google.co.kr 접속 오류

    ***해결 과정*** : 방화벽 컴퓨터 구현하기 - Server 설정 (정책 2)단계에서 google.co.kr에 접속하려 시도<br>
             -> ping을 날려 연결 확인을 해본 결과 문제 없음<br>
             -> 방화벽 확인했으나 문제 없음<br>
             -> 이유는 Client 에서 인터넷 접속을 확인해야했는데 Server에서 확인하려했기 때문<br>
             -> '내부 컴퓨터는 외부 인터넷을 사용할 수 있도록 한다.' 의 조건에 따라 규칙을 추가하고 마스커레이드를 허가했기 때문에 Client 에서 확인해야 잘 작동됨<br>
             -> Client 서버로 인터넷에 접속해 오류 해결

- **172.16.1.20 접속 오류**

    ![오류2_1](https://user-images.githubusercontent.com/77660379/120384904-b7edef80-c361-11eb-80a6-327edb5da21b.JPG)

    ![오류2](https://user-images.githubusercontent.com/77660379/120384898-b6242c00-c361-11eb-92f8-604ea2b7bf54.JPG)

    ![오류2해결1](https://user-images.githubusercontent.com/77660379/120384907-b7edef80-c361-11eb-9c8c-9857cdd051f8.JPG)

    ***문제발생 및 고민한 내용*** : 172.16.1.20 접속 오류

    ***해결 과정*** : Host Computer 에서 Server(b) ip 주소로 접속 시도<br>
             -> 웹페이지 접속 안됨
             -> Windows Powershell을 통해 Server(b)의 ip 주소인 '172.16.1.20' 으로 ping을 날려보니 연결 안됨
             -> Serevr(b), Client, Server에 '172.16.1.20'dmfh ping을 날려 연결 확인을 해본 결과 문제 없음<br>
             -> 무언가 잘못되었음을 인지<br>
             -> 강의자료와 강의를 다시 돌려보며 실습과제를 다시 이해하는 시간을 가짐<br>
             -> 인터넷과 가상 허브를 잇는 것은 Server의 역할임을 이해함<br>
             -> Server(b)는 웹 서버 구축과 wordpress 설치에 이용되는 서버이며, 접속 ip는 Server이어야 함을 깨닫게 됨<br>
             -> Windows Powershell에 linux로 원격접속한 후 Server이 ip 주소로 접속해 오류 해결

* ### **참고할 만한 내용**

 * #### **VM ware 설정 - NAT / Bridged** <br>

  * NAT
   
    ![NAT](https://user-images.githubusercontent.com/77660379/120384002-917b8480-c360-11eb-81e0-197a754836c7.JPG)

    *NAT으로 설정되어 있는 경우*
    => VM ware 가 설치된 컴퓨터를 마치 공유기처럼 사용하겠다는 의미<br>
      -> 따라서 NAT로 Network Adapter사 설정된 경우, 리눅스나 윈도우에서 IP주소를 변경할 필요가 없음
         내 컴퓨터에서 리눅스 IP로 통신할 수 있는 일종의 우체국 기능을 제공하기 때문 <br>

  * Bridged
   
    ![Bridged](https://user-images.githubusercontent.com/77660379/120384010-94767500-c360-11eb-9454-f1f20dbb869e.JPG)

    *Bridged로 설정되어 있는 경우*
    => 리눅스 IP를 공유기 내부 IP로 설정하는 것도 가능하다는 의미<br>
      -> 즉 리눅스가 실제 구동되고 있는 곳은 '내 컴퓨터' 지만, IP는 마치 공유기 내부 IP중 하나를 사용하도록 만드는 것
         이 경우 '내 컴퓨터'의 IP Network ID와 동일하고, Host ID는 상이하도록 리눅스 IP를 수정해주면 됨

    [리눅스 IP 변경 및 네트워크 설정](https://whitewing4139.tistory.com/95)

    [NAT와 Bridged Networking 개념 정리](https://itmore.tistory.com/entry/NAT-%EC%99%80-Bridged-Networking-%EA%B0%9C%EB%85%90-%EC%A0%95%EB%A6%AC)

* ### **회고 (+,-,!)**

1. ***뿌듯했던 점 (+)***
    => 내부/외부 컴퓨터 간의 접속을 제어할 수 있다는 점이 흥미로웠다. 뿐만 아니라 방화벽이라고는 ufw 로 설정하는 것만 있는 줄 알았는데 이번 주차에 이렇게 여러가지를 배우고나니 리눅스와 보다 가까워진 것 같아 뿌듯했다. 비록 Server, Server(b), Client, Windows Powershell을 전부 이용하다보니 ip주소가 헷갈리기도 했지만 큰 오류 없이 마무리해서 다행이라고 생각했다. 이렇게 리눅스에 대해 이제 막 재미를 붙이기 시작했는데 벌써 수업이 마무리 된다니 한편으로는 아쉽기도 하다. 기말고사까지 오류없이 재미있게 끝마칠 수 있으면 좋겠다.<br>
       
2. ***보완할 점 (-)***
    => 강의 내용을 충분히 이해한 후 실습 과제를 진행해야함을 느꼈다. 이번 주차의 실습은 강의 내용을 이해하면 전혀 헤맬 필요가 없는 난이도였다. 그러나 내부/외부 컴퓨터 간의 관계를 완벽히 이해하지 못하고 과제를 시작해서 였는 지 Host Computer에서 접속하는 부분에서 몇시간이나 낭비했다. 그래도 기말고사 전에 내가 헷갈려하는 부분은 어디인지 알게 됐고 11, 12, 13 주차 강의자료를 찾아보며 복습하고나니 이번 과제 때문에 허덕인 시간이 아깝지만은 않았다. 아직 부족한 부분이 여러군데 있는 것 같으므로 지난 주차들 수업을 다시 반복해 공부해야겠다.<br>
 
3. ***꼭 기억할 점 (!)*** 
    => 이번 14주차에서는 방화벽과 방화벽의 정책에 대해서 꼭 기억했으면 해서 정리하고자 한다. 방화벽이라는 것이 무엇을 차단하는 것인지. 컴퓨터로 위험한 무언가가 흘러 들어온다는 의미는 크게 두가지이다. 첫째, USB나 CD처럼 특정 저장 매체 내에 존재하는 악성 프로그램이 직접 유입되는 경우. 둘째, 외부 인터넷과 연결된 LAN선으로 악성 프로그램이 유입되는 경우. *방화벽의 경우 후자의 상황이 벌어지는 것을 방지한다.*<br>
        -> 통신 시 생성되는 패킷의 내용을 확인하여 해당 패킷을 통과시킬지 차단할지 판단<br>
    리눅스 방화벽 정책 못록 : Chain
        -> 윈도우에서 방화벽의 정책 종류는 인바운드와 아웃바운드에 대한 정책 2가지 존재 / 리눅스 역시 내 컴퓨터로 들어오는 통신과, 내 컴퓨터에서 나가는 통신에 대한 정책 존재
          윈도우에서 정책이라고 사용하는 단어를 리눅스 방화벽에서는 체인(Chain) 이라는 용어로 사용함
          INPUT, OUTPUT, FORWARD
          INPUT과 OUTPUT : 윈도우 방화벽의 인바운드와 아웃바운드에 해당하는 개념
          FORWARD의 경우 내 리눅스 PC를 경유하는 패킷에 대한 정책을 정의하는 Chain, 리눅스 시스템을 이용하는 네트워크 장비(스위치, 라우터 등)에 많이 사용하며, 서버처럼 말단에 위치한 리눅스의 경우, FORWARD 정책을 사용할 일이 거의 없음 


    [리눅스 방화벽, 방화벽 서비스 및 정책 확인](https://whitewing4139.tistory.com/124)
