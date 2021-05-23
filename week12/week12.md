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
    문제발생 및 고민한 내용 : SSH 접속 RSA 공유키 충돌오류

    해결 과정 : ssh@linux* 로 접속 시도
             -> '중간자 공격'에 대한 경고창 발생
             -> 이유는 같은 IP 로 기존에 접속한 적이 있는 서버와 RSA 공유키를 교환한 상태에서, 서버가 바뀌었기 때문
             -> 이 경우는 운영자인 내가 고의적으로 변경한 것이기에, 해킹 등의 침해사고는 아님(스푸핑 X)
             -> ssh-keygen -R* 명령어를 통해 초기화시켜 오류 해결
    ````
    [RSA 공유키 충돌오류 참고](https://cpuu.postype.com/post/30065)

- **라운드 로빈 방식의 웹 서버 구현 오류**

    ![오류2구동](https://user-images.githubusercontent.com/77660379/117954538-140cb780-b352-11eb-9a8d-e5175dff75bb.JPG)

    ![오류2변경안됨](https://user-images.githubusercontent.com/77660379/117954548-166f1180-b352-11eb-8048-d04d92dfd55e.JPG)

    ![오류2해결](https://user-images.githubusercontent.com/77660379/117954552-1707a800-b352-11eb-90bc-7666e3daa6de.JPG)

    ```
    문제발생 및 고민한 내용 : nslookup 도메인 주소 출력 오류

    해결 과정 : 기존의 구축된 웹 서버의 IP 주소 3개 확인 시도
               -> nslookup을 통해 인터파크, 알라딘, 파리바게트 3개의 IP주소를 확인하려 했으나 변경이 안되어있음
               -> 변경 사항을 저장하기 위한 restart 작업을 건너뛴 것이 문제였음
               -> systemctl restart named 명령어를 통해 네임 서버를 다시 가동시켜 오류 해결
    ````
    [nslookup 도메인 주소 출력 오류 참고](https://www.digitalocean.com/community/questions/sudo-ufw-status-return-inactive)


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