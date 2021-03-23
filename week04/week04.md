# 20200994 배서은
**컴퓨터시스템관리 4주차 실습일지**

---
#### 4주차에는 
1. 리눅스 기본 프로그램 사용
2. X 윈도우의 개념 이해
3. 다양한 방법으로 응용 프로그램 설치
4. 다양한 데스크톱 환경 설치
---

## 1. 실습과제 결과

* ### **Server(b)에 GNOME 데스크톱 설치 후, 유용한 프로그램 3개 설치**
  
  **CHECK POINT** <br>
  *우분투에 Chrome을 설치하면 다른 프로그램들을 다운로드하기 보다 유용해진다*

* ### **Chrome 설치** <br>
  
  * Chrome 소개

    ```
    Google Chrome은 구글이 개발중인 프리웨어 웹 브라우저
    크롬이란 뜻은 본래 그래픽 사용자 인터페이스 에서 창틀을 가리키는데, 여기서는 브라우저 틀 영역을 가리키며, 이 영역을 최소화시키자는 목표로 크롬이라고 이름을 지었다고 함
    스탯 카운터 통계 기준으로 2012년 5월부터 인터넷 익스플로러를 제치고 현재 전 세계에서 가장 많이 쓰이는 웹 브라우저
    ```

  * Chrome이 유용하다고 생각한 이유

    ```
    우분투에 기본적으로 firefox 라는 웹 브라우저가 탑재되어 있지만 보다 익숙해 편리한 Chrome이 설치된다면 유용할 것이라 생각
    ```

  - 터미널 창에 크롬 브라우저 패키지 설치용 인증키를 받기 위한 명령어 입력, 크롬 웹 브라우저 패키지를 다운로드 받을 PPA를 sources.list.d 에 추가

    ![chrome1](https://user-images.githubusercontent.com/77660379/112141098-3b7bb980-8c18-11eb-8b55-81a70df88ce9.JPG)

  - 패키지 리스트 업데이트

    ![chrome2](https://user-images.githubusercontent.com/77660379/112141161-4d5d5c80-8c18-11eb-9cc2-f4f0f55bf851.JPG)
    
  - 크롬 설치

    ![chrome3](https://user-images.githubusercontent.com/77660379/112141200-5b12e200-8c18-11eb-8784-19209fdf17c5.JPG)
  
  - 크롬 설치를 위해 생성했던 파일 제거

    ![chrome4](https://user-images.githubusercontent.com/77660379/112141312-7aaa0a80-8c18-11eb-9550-584efb76e85f.JPG)

  - 크롬 설치 완료

    ![chrome설치완료](https://user-images.githubusercontent.com/77660379/112141393-93b2bb80-8c18-11eb-8833-d9105c14b633.JPG)

    ![완료](https://user-images.githubusercontent.com/77660379/112141487-ae853000-8c18-11eb-92d3-87587b88938d.JPG)


* ### **Visual Studio Code 설치** <br>

  * Visual Studio Code 소개

    ```
    Visual Studio Code는 마이크로소프트가 마이크로소프트 우니도우, macOS, 리눅스용으로 개발한 소스 코드 편집기
    디버깅 지원과 Git 제어, 구문 강조 기능등이 포함되어 있으며, 사용자가 편집기의 테마와 단축기, 설정 등을 수정 가능
    ```

  * Visual Studio Code가 유용하다고 생각한 이유

    ```
    윈도우에서 git에 코드를 연동할 때 visual studio code를 사용하는데, 리눅스에도 vscode가 탑재된다면 vim 보다 훨씬 편리해 유용할 것이라 생각
    ```

  - Visual Studio Code 사이트에 접속해 Visual Studio Code 다운로드

    ![vscode1](https://user-images.githubusercontent.com/77660379/112142194-9b269480-8c19-11eb-876a-663518d2220b.JPG)


  - 그 중 리눅스 > 우분투에 설치할 것이므로 deb 파일 64bit를 다운로드

    ![vscode2](https://user-images.githubusercontent.com/77660379/112142281-b6919f80-8c19-11eb-9627-1c897fe5d239.JPG)

  - Keep 클릭

    ![vscode3](https://user-images.githubusercontent.com/77660379/112142311-c315f800-8c19-11eb-8240-34d2a46cf6a2.JPG)

  - 터미널 창에서 ~/Downloads 디렉터리에 code_1.38.0*.deb파일이 다운로드 되어있는 지 확인

    ![vscode4](https://user-images.githubusercontent.com/77660379/112142346-cf01ba00-8c19-11eb-9859-a8a66636a715.JPG)

  - code_1.38.0*.deb파일이 있는 디렉터리로 이동하여 설치

    ![vscode5](https://user-images.githubusercontent.com/77660379/112142389-de810300-8c19-11eb-8eb0-12d5299d2dd2.JPG)

  - Visual Studio Code 설치 완료

    ![vscode6](https://user-images.githubusercontent.com/77660379/112142485-01131c00-8c1a-11eb-956b-d8f8f5bba94e.JPG)

 ### **Kakaotalk 설치** <br>
  
  * Kakaotalk 소개

    ```
    KakaoTalk은 전세계 어디서나 안드로이드폰과 아이폰 사용자간 무료로 메시지를 주고 받을 수 있는 메신저 서비스
    ```

  * Kakaotalk이 유용하다고 생각한 이유

    ```
    대부분의 이용자가 윈도우에 PC 카카오톡을 필수로 설치해 사용
    때문에 우분투에서도 윈도우 환경에서와 마찬가지로 PC 카카오톡이 설치된다면 유용할 것이라 생각
    ```

  - wine, playonlinux 설치

    ![오류해결1](https://user-images.githubusercontent.com/77660379/112161716-bf40a080-8c2e-11eb-9725-16764df3f56a.JPG)

  - PlayOnLinux 실행 > Wine 버전 관리 확인 > 안정화 버전인 wine 5.0.2 확인

    ![오류해결2](https://user-images.githubusercontent.com/77660379/112161769-cb2c6280-8c2e-11eb-9684-149a5bb69392.JPG)

    ![오류해결3](https://user-images.githubusercontent.com/77660379/112162308-48f06e00-8c2f-11eb-9813-ad6245237e9b.JPG)

    ![오류해결4](https://user-images.githubusercontent.com/77660379/112162373-57d72080-8c2f-11eb-8a46-7ddd1f473656.JPG)

  - wine 5.0.2 설치 > 'Install a non-listed program' 클릭 > '다음' 클릭

    ![오류해결5](https://user-images.githubusercontent.com/77660379/112162627-9076fa00-8c2f-11eb-9253-7dcc5bfd7eff.JPG)

    ![오류해결6](https://user-images.githubusercontent.com/77660379/112162688-a08ed980-8c2f-11eb-8f54-a2222da70eaa.JPG)

  - 'Install a program in a new virtual drive' 클릭 > 'kakao' 이름 정해줌 > 세 개 모두 선택

    ![오류해결7](https://user-images.githubusercontent.com/77660379/112163014-f2cffa80-8c2f-11eb-9bbc-a9ed0a47df56.JPG)

    ![오류해결8](https://user-images.githubusercontent.com/77660379/112163057-024f4380-8c30-11eb-938c-b84fce46a38e.JPG)

    ![오류해결9](https://user-images.githubusercontent.com/77660379/112163182-201ca880-8c30-11eb-8290-935dc4488d35.JPG)

  - 설치 확인했던 wine 5.0.2 선택 > 32비트 선택

    ![오류해결10](https://user-images.githubusercontent.com/77660379/112163352-49d5cf80-8c30-11eb-94c4-a2ae11a5526b.JPG)

    ![오류해결11](https://user-images.githubusercontent.com/77660379/112163409-5823eb80-8c30-11eb-8274-74078ae12050.JPG)

  - mono 설치 > window 10 선택 > gdiplus, gecko, mono28 선택

    ![오류해결12](https://user-images.githubusercontent.com/77660379/112163606-899cb700-8c30-11eb-8a95-71260fd3dc41.JPG)

    ![오류해결13](https://user-images.githubusercontent.com/77660379/112163667-97523c80-8c30-11eb-971f-90c3d60ac1b0.JPG)

    ![오류해결14](https://user-images.githubusercontent.com/77660379/112163720-a20cd180-8c30-11eb-92b3-6ca26861bb69.JPG)

  - Chrome을 통해 카카오페이지로 이동 후 카카오톡 설치 

    ![오류해결15](https://user-images.githubusercontent.com/77660379/112164066-ef893e80-8c30-11eb-8cf3-991296b3fc51.JPG)

  - PlayOnLinux 찾아보기에서 다운로드한 카카오 설치 파일 선택

    ![오류해결16](https://user-images.githubusercontent.com/77660379/112164289-1b0c2900-8c31-11eb-9f51-08c451829f57.JPG)

  - 카카오 설치 화면 > 윈도우에서 설치하던 방법과 동일하게 설치 (단, 마지막에 '카카오톡 실행'만 체크 해제)

    ![오류해결18](https://user-images.githubusercontent.com/77660379/112164603-5dce0100-8c31-11eb-9978-0a36219872b6.JPG)

    ![오류해결19](https://user-images.githubusercontent.com/77660379/112164677-6cb4b380-8c31-11eb-9d2b-8010c54e3d39.JPG)

  - 카카오톡을 선택해서 바로가기 생성 > 표시될 이름 'KakaoTalk'으로 설정

    ![오류해결20](https://user-images.githubusercontent.com/77660379/112164903-9f5eac00-8c31-11eb-9d2e-c2482b5db901.JPG)

    ![오류해결21](https://user-images.githubusercontent.com/77660379/112164965-ad143180-8c31-11eb-9f2c-e99178bce651.JPG)

    ![오류해결22](https://user-images.githubusercontent.com/77660379/112165113-cb7a2d00-8c31-11eb-97b0-673f09c88cda.JPG)

  - 카카오톡 실행

    ![오류해결23](https://user-images.githubusercontent.com/77660379/112165172-d9c84900-8c31-11eb-8a46-b4d16d8a293a.JPG)

    ![kakaosolve](https://user-images.githubusercontent.com/77660379/112165792-66730700-8c32-11eb-8e7d-a89fcbaa46be.jpg)

## 2. 실습과제 Review

* ### **새로 배운 내용**
```
1. Files 파일
    => GNOME 데스크톱의 기본 파일 관리자(GNOME 의 이전 파일 관리자는 미드나잇 커맨더)
       내부적으로는 노틸러스 nautilus 라고 부르기도 함
       2001년 처음 공개, 현재 GNU LGPL 로 관리
       3.18 버전 부터 구글드라이브 연동 가능 (Dropbox, Own Cloud 도 가능)
       Uvuntu 20.04 LTS 에서는 3.36.3-stable 버전이 기본으로 설치되어 있음

2. 데스크톱 환경 - GNOME
    => 그놈 GNOME, GNU Network Object Model Environment
       데스크톱 프로그램 집합의 일종이자 이를 개발하는 프로젝트 이름

3. X 윈도우
     => 유닉스 계열 운영체제에서 사용되는 윈도우 시스템
        디스플레이 장치에 창(윈도우)을 표시하며, 마우스와 키보드 등 입력장치의 상호작용을 관리해 GUI 환경 구현을 위한 기본적인 프레임워크 제공
        1984년, MIT에서 개발
        1987년, X윈도우 시스템 프로토콜의 가장 최신 버전 개발, X11
        현재는 X.Org 재단에서, 오픈소스라이선스로 배포 및 관리
        네트워크 프로토콜 기반의 클라이언트-서버 모델
        UI(User-Interface) 의 모습에 관여하지 않음
        다양한 모습의 데스크톱 환경(KDE, GNOME, Xface 등)이 X윈도우를 기반으로 사용함
```

* ### **문제가 발생하거나 고민한 내용 + 해결 과정**

- **Tasksel 패키지 설치 오류**

    ![오류0](https://user-images.githubusercontent.com/77660379/112175251-75f64e00-8c3a-11eb-921a-8b41d20fe8aa.JPG)

    ![오류1](https://user-images.githubusercontent.com/77660379/112175323-83133d00-8c3a-11eb-97b8-9a6257c2f1f7.JPG)

    ![오류2](https://user-images.githubusercontent.com/77660379/112175391-8dcdd200-8c3a-11eb-8483-b238510bc528.JPG)

    ![해결](https://user-images.githubusercontent.com/77660379/112175445-97efd080-8c3a-11eb-8c56-27cd640501b6.JPG)

    ![해결완료](https://user-images.githubusercontent.com/77660379/112175528-a76f1980-8c3a-11eb-8827-1eb0b31ca0d9.JPG)

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

- **KakaoTalk XP버전 다운 불가**

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