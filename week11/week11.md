# 20200994 배서은
**컴퓨터시스템관리 11주차 실습일지**

---
#### 11주차에는 
1. 네임 서버의 작동 방식 이해
2. 캐싱 전용 네임 서버 구축
3. 라운드 로빈 방식의 네임 서버 구축
---

## 1. 실습과제 결과

* ### **라운드 로빈 방식의 네임 서버 구현**
  
* #### **client의 웹 브라우저에서 "seoeun.com" 으로의 접속 장면과 "seoeun.com" 으로 질의하여 입력된 ip 주소 확인** <br>
    
  * client의 웹 브라우저에서 seoeun.com 으로의 접속 장면
    <br>

    [www.seoeun.com 접속 실습 영상](https://baedevelog.tistory.com/9)
    <br><br>

  * nslookup > seoeun.com
    <br>

    ![1도메인](https://user-images.githubusercontent.com/77660379/117953768-51bd1080-b351-11eb-90ea-28d2f0b53455.JPG)
    <br><br>

    *인터파크* -> Adress : 121.254.157.38
    *알라딘* -> Adress : 211.111.219.12
    *파리바게트* -> Adress : 13.125.57.70
    <br><br>
     
## 2. 실습과제 Review

* ### **새로 배운 내용**

```
1. Domain Name System, DNS
    => 도메인 네임 시스템, 네임서버
       -> 호스트의 도메인 이름을 호스트의 네트워크 주소로 바꾸거나. 그 반대의 변환을 수행
          네트워크 상에서 컴퓨터를 식별하는 호스트명
          좁은 의미로, 도메인 레지스트리에 등록된 이름
          우분투는, BIND를 사용
       Local Name Server
       -> /etc/resolv/conf 에서 nameserver IP 로 설정된 서버
       nslookup (name server lookup)
       -> 네트워크 과리 명령 줄 인터페이스 도구

2. Catching only name server
    => PC 에서 URL 로 IP 주소를 얻고자 할 때, 해당하는 URL 의 IP 주소를 알려주는 네임 서버 

3. Round Robin DNS
     => Master Nmae Server 마스터 네임 서버
        -> 컴퓨터 ip주소를 알기 원할 떄 해당 컴퓨터의 IP 주소를 알려주는 네임 서버

        Round Robin 라운드 로빈
        -> 여러 대의 웹 서버를 운영하여 웹 클라이언트가 서비스를 요청할 경우 교대로 서비스를 실행하여, 웹 서버의 부하를 공평하게 나누는 방식
```

* ### **문제가 발생하거나 고민한 내용 + 해결 과정**

- **SSH 접속 RSA 공유키 충돌오류**

    
    ![오류1](https://user-images.githubusercontent.com/77660379/117954405-f2133500-b351-11eb-94d2-ff01963e3f44.JPG)

    ![오류해결](https://user-images.githubusercontent.com/77660379/117954415-f4758f00-b351-11eb-9a95-5523cd2ccc74.JPG)

    ![오류해결완료](https://user-images.githubusercontent.com/77660379/117954419-f5a6bc00-b351-11eb-9cb0-52a4c7f8ce14.JPG)

    ```
    문제발생 및 고민한 내용 : server 가상 머신 실행 오류

    해결 과정 : Server 가상 머신 재설치
             -> 지난 9주차에 server를 이용하느라 백업폴더에 따로 보관해두었는데 이번에 사용하려하니까 찾을 수 없다는 오류 발생
             -> 재설치하면서 오류 해결
    ````
    [RSA 공유키 충돌오류 참고](https://cpuu.postype.com/post/30065)

- **라운드 로빈 방식의 웹 서버 구현 오류**

    ![오류2구동](https://user-images.githubusercontent.com/77660379/117954538-140cb780-b352-11eb-9a8d-e5175dff75bb.JPG)

    ![오류2변경안됨](https://user-images.githubusercontent.com/77660379/117954548-166f1180-b352-11eb-8048-d04d92dfd55e.JPG)

    ![오류2해결](https://user-images.githubusercontent.com/77660379/117954552-1707a800-b352-11eb-90bc-7666e3daa6de.JPG)

    ```
    문제발생 및 고민한 내용 : dconf-editor 오류

    해결 과정 : dconf-editor 명령어에서 화면창을 띄울 수 없다는 오류창이 발생함
               -> xhost로 실행시키는 방법 시도했으나 해결 안됨
               -> dconf-editor는 root가 아닌 사용자 계정에서 실행해야함
               -> root의 권한에서 dconf-editor를 실행하려하니까 오류가 반복 된 것
    ````
    [nslookup 도메인 주소 출력 오류 참고](https://www.digitalocean.com/community/questions/sudo-ufw-status-return-inactive)


* ### **참고할 만한 내용**

  * Telnet & SSH & VNC

    [Telnet & SSH & VNC](https://kimhyun2017.tistory.com/33)

    ```
    Telnet
    => 오랫동안 전통적으로 사용되어 온 원격 접속 방법
       보안에 취약함
       Telnet 서비스를 이용하려면 원격지에서 접속할 pc는 클라이언트가 필요
       TCP/IP 기반의 프로토콜로 원격지 시스템을 자신의 시스템처럼 사용할 수 있게 하는 원격 터미널 접속 서비스
       TCP/23번 포트 사용
       Plain Text

    SHH
    => Telnet과 용도는 동일하나 Telnet의 약점인 보안성을 강화한 것
       데이터를 전송할 떄 암호화한 데이터로 전송
       기본적으로 centOS에서 패키지 설치나 방화벽 허용이 되어있음

    VNC
    => X윈도우 환경으로 원격접속을 하고싶을 때 사용
       원격지로 그래픽 화면을 전송하는 원리이므로 속도가 많이 느림
    ```

* ### **회고 (+,-,!)**

1. *뿌듯했던 점 (+)*
    => 원격 접속에 흥미를 느낀 것
          -> 이번 주차는 새롭게 배운 원격 접속이 재미있게 느껴졌다. 서버와 클라이언트의 관계를 이해하는 데에 더욱 도움이 되기도 했고 내 컴퓨터로 내 컴퓨터의 다른 서버에 원격으로 접속해보다니 신기하기도 했다. 컴퓨터는 알면 알수록 매력있는 것 같다. 앞으로의 실습 역시 기대된다.<br>
       
2. *보완할 점 (-)*
    => 백업 파일 관리
      -> 이번 주차 실습은 비교적 수월했고, 원격 접속이라는 실습이 굉장히 흥미롭게 느껴졌다. 그러나 백업 파일을 다시 불러오는 과정에 있어 오류가 생겨 시간을 많이 빼앗겼다. 우선 server(b)의 경우 언제 한번 재설치를 다시 해야겠다고 벼르고 있었는데 그게 이번이 되었다. 지금까지는 그래도 오류 없이 작동되어서 문제가 없엇는데 ifupdown 명령어 실행에 있어 오류가 반복적으로 발생했기 때문이다. 또 하나는 server의 경우인데 지난 주 실습 떄문에 따로 보관해둔 server 폴더에 오류가 생겼는 지 not found 오류로 가상머신이 실행 조차 되지 않았다. 결국 server와 server(b) 모두 재설치하게 된 것이다. 그래도 시간을 들여 재설치 해놨으니 남은 주차의 실습에서 백업 및 재설치 관련 문제로 시간 낭비할 일은 없을 것 같다.<br>
 
3. *꼭 기억할 점 (!)* 
    => Telnet, SHH, VNC server 각각의 특징, 차이점 파악
         -> 이번 주차에서 가장 중요한 부분이 아닐까 싶다. 수업 내용 뿐만 아니라 따로 내용을 더 찾아보았는데, 그래도 확실히 공부하기 위해서 복습을 다시 해봐야겠다.