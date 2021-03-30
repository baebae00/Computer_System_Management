# 20200994 배서은
**컴퓨터시스템관리 5주차 실습일지**

---
#### 5주차에는 
1. 리눅스에서 다루는 파일시스템과 하드디스크의 구조 이해
2. 하나의 하드디스크 추가
3. 여러 개의 하드디스크를 하나의 하드디스크 처럼 사용
---

## 1. 실습과제 결과

* ### **Server(b)에 RAID 구축**
  
* ### **RAID 1 설치** <br>
  
  * RAID 1 을 선택한 (가장 적절하다고 생각한) 이유

    ```
    가용성 높음 + 복원이 비교적 매우 간단 => RAID 1

    비록 빠른 속도는 기대할 수 없지만 하드디스크가 고장나더라도 없어져서는 안될 중요한 데이터는 안전하게 복구할 수 있다는 점에서 가장 맘에 듦
    ```

  - 하드디스크 파티션 (b, c 생성 후 이를 이용해 RAID 생성)

    ![하드디스크파티션](https://user-images.githubusercontent.com/77660379/113011800-1c9b9b00-91b5-11eb-85f6-647e4295f6b1.JPG)

  - RAID 1 구성

    ![raid1](https://user-images.githubusercontent.com/77660379/113011849-291ff380-91b5-11eb-8c0d-16bfcadcfdaf.JPG)
    
  - 정보 확인

    ![raid1_2](https://user-images.githubusercontent.com/77660379/113011900-363ce280-91b5-11eb-927e-05eb69293cb9.JPG)


## 2. 실습과제 Review

* ### **새로 배운 내용**
```
1. 리눅스의 파일 시스템
    => 디렉터리 Directory
        -> 파일(또는 다른 디렉터리)을 보관하는 특수한 파일
           다른 디렉터리에 존재하는 파일 이름은 동일해도 됨 (접근 가능)
       트리 구조
       
       파일 시스템의 종류
         -> ext4, XFS, Btrfs, ...
            저장장치의 데이터 구조, 처리하는 프로그램이 다름
            동일한 시스템 콜을 호출하여 통일된 인터페이스로 접근 가능

       데이터와 메타데이터
         -> 데이터 : 특정 목적에 따라 생성된 실제 데이터
            메타 데이터 : 데이터의 정보(이름, 위치, 크기, 종류, 생성시간, 권한 등)를 담은 데이터

2. 하드디스크 추가
    => SATA(Serial ATA, 직렬 ATA)
        -> 하드디스크 또는 광학 드라이브와 데이터 전송을 주요 목적으로 만든 컴퓨터 버스
       
       SCSI(Samll Computer System Interface)
         -> 컴퓨터에 주변기기를 연결할 때 직렬 방식으로 연결하기 위한 표준

       파티션(Partician)
         -> Primary 파티션 / Extended 파티션 / Logical 파티션
            1개의 하드디스크는 4개의 Primary 파티션까지 설정 가능 (5개의 파티션을 설정하려면, 3개의 Primary 파티션과 1개의 Extended 파티션을 설정한 뒤, Extended 파티션을 2개 이상의 Logical 파티션으로 설정)

3. 여러 개의 하드디스크를 하나처럼 사용
     => RAID(Redundant Array of Inexpensive/Independent Disks)
          -> 여러 개의 하드디스크를 하나의 하드디스크 처럼 사용하는 방식
             비용, 신뢰성, 성능 조절의 효과
             하드웨어 RAID : 하드웨어 제조업체에서 여러 개의 하드디스크를 연결한 장비를 만들어서 공급
             소프트웨어 RAID : 운영체제에서 지원하는 방식
```

* ### **문제가 발생하거나 고민한 내용 + 해결 과정**

- **tldr 오류**

    ![tldr 오류](https://user-images.githubusercontent.com/77660379/113012440-bcf1bf80-91b5-11eb-8876-6df630700ae9.JPG)

    ![tldr 해결](https://user-images.githubusercontent.com/77660379/113012486-c7ac5480-91b5-11eb-95ff-8849cf12fe08.JPG)

    ```
    문제발생 및 고민한 내용 : 현재 카카오에서 XP버전을 배포하지 않아 카카오톡 XP버전 다운 불가

    해결 과정 : cobextract, winetricks, winetricks 모듈 설치 후 kakaotalk XP버전을 다운 받을 수 있는 링크로 접속
               -> wine[카카오톡설치파일] 명령어를 터미널 창에 입력했으나 'not found' 오류 
               -> 터미널 창을 닫고 다시 터미널 창을 열어 skel 디렉터리를 비우려고 시도했으나 불가능
               -> Server(b)에 설치해 둔 Chrome을 이용해 카카오페이지에 접속함
               -> kakaotalk 신규 버전 다운로드
               -> wine, playlinux를 이용한 설치로 다운로드 방법 변경
               -> PlayOnLinux를 실행해 Wine을 설치하므로써 문제 해결
    ````

- **mdadm 오류**

    ![kakao9](https://user-images.githubusercontent.com/77660379/112167980-42b0c080-8c34-11eb-9ac6-532d44a9db0d.JPG)

    ![kakao10](https://user-images.githubusercontent.com/77660379/112168040-4f351900-8c34-11eb-9e69-67f973d23a63.JPG)

    ![kakao11](https://user-images.githubusercontent.com/77660379/112168102-5b20db00-8c34-11eb-8630-3d50d99a76f1.JPG)

    ![kakao12](https://user-images.githubusercontent.com/77660379/112168163-670c9d00-8c34-11eb-9cdd-f10b60047fb7.JPG)

    ![kakao13](https://user-images.githubusercontent.com/77660379/112168242-75f34f80-8c34-11eb-9216-345cc4045474.JPG)

    ![오류1](https://user-images.githubusercontent.com/77660379/112168342-8f949700-8c34-11eb-9d11-09ff9c621049.JPG)

    ```
    문제발생 및 고민한 내용 : Tasksel 로 페키지 설치 단계에서 작동 오류

    해결 과정 : tasksel 실행 > Ubuntu desktop 선택 > <ok> 선택 후 엔터
               -> 터미널 창으로 커서가 넘어가 어떠한 키를 누르던 이상한 문자가 출력됨 
               -> Esc 키로 터미널 창을 닫으려 시도했으나 불가능
               -> 마우스로 Poweroff 강제종료 시킴
               -> 다시 한번 시도했으나 이전과 같은 문제 발생, 창이 멈춤
               -> 다시 한번 시도하고 터미널 창으로 커서가 넘어갔어도 기다림
               -> 오랫동안 기다리니 패키지 설치 창으로 넘어가 자동으로 설치 진행됨
    ````

* ### **참고할 만한 내용**
```
gftp란?
    gftp는 무료/오픈 소스 멀티 스레드 파일 전송 프로토콜 클라이언트 프로그램
    FTP, FTPS, HTTP, HTTPS, SFTP 및 FSP 프로토콜뿐만 아니라 FTP 및 HTTP 프록시 서버 지원 및 FXP 파일 전송(FTP를 통해 두 원격 서버 간에 파일 전송)에 대한 지원이 있음
    GTK+를 사용해 만든 X 윈도우용 FTP클라이언트 프로그램
    GUI 형태로 되어 있어 windows를 주로 사용하는 이용자들에게 편리

gtfp의 특징
    파일전송중 인터럽트된 파일의 이어받기 가능, 동시 다운로드 가능, FTP,HTTP,SSH 프로토콜 지원, 파일 전송 큐, 디렉터리 전체받기 가능, FTP 와 HTTP 프록시 지원, 원격 디렉터리 캐시, 드래그앤드롭 지원, 매우 뛰어난 접속 매니저 등 의 다양한 기능이 있음
```

* ### **회고 (+,-,!)**
```
1. 뿌듯했던 점 (+)
    => 오류가 발생했을 때 스스로 문제 해결 방법을 찾은 것
          -> 카카오톡 설치 방법이 한가지가 아니기 때문에 XP 배포판이 사라진 현재, wine과 playonlinux를 활용한 방안으로 설치 방향 바꿈

2. 보완할 점 (-)
    => 오류가 발생했을 때 바로 강제종료 버튼을 눌렀던 점
      -> 오류가 발생할 경우 기다려보기

3. 꼭 기억할 점 (!) 
    => GNOME(GNU Network Object Model Environment)은 사용자가 컴퓨터를 쉽게 사용하고 설정할 수 있도록 해주는 친숙한 데스크톱 환경
       데스크톱 프로그램 집합의 일종이자 이를 개발하는 프로젝트의 이름
       기본적으로 C로 작성되었으나 C++, java, ruby, c#, python 등 많은 언어들에 대한 바인딩이 존재하기 때문에 C를 사용하지 않는 개발자라도 자신에게 맞는 언어로 그놈에서 사용하는 응용 프로그램을 작성할 수 있음