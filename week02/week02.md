# 20200994 배서은
**컴퓨터시스템관리 2주차 실습일지**

---
#### 1주차에는 
1. 컴퓨터 시스템의 기본 구조와 운영체제의 역할 이해
2. 리눅스가 설치된 컴퓨터를 사용하기 위한 기본 방법 이해
3. 시스템 관리자로서 기본적인 리눅스 명령어를 실습
---

## 1. 실습과제 결과

* ### **리눅스 기본 명령어 중 잘 모르는 3개를 선정 후 각각의 man 페이지를 OO_man.txt 파일로 저장한 뒤, 자신의 학번으로 압축**
  
  **CHECK POINT** <br>
  *vmware 가상환경의 firefox웹사이트를 이용하면 실제 pc 환경과 연동시키지 않아도 파일을 업로드 할 수 있다*

* ### **man.txt파일 -> tar.gz압축** <br>
    [20200994.tar.gz URL](https://baedevelog.tistory.com/6)

  - man less

    ![man less](https://user-images.githubusercontent.com/77660379/111018670-7f431780-83fd-11eb-87c3-12e49cba1e32.JPG)
  
  - man more
      
    ![man more](https://user-images.githubusercontent.com/77660379/111018706-b9141e00-83fd-11eb-9074-36379f4c51c2.JPG)
  
  - man mount
      
    ![man mount](https://user-images.githubusercontent.com/77660379/111018710-c7fad080-83fd-11eb-9f2a-88cbacf43d7c.JPG)

* ### **실습 과정**
  - test 내 파일 삭제

    ![test 내 파일 삭제](https://user-images.githubusercontent.com/77660379/111018888-296f6f00-83ff-11eb-8363-16113050ea85.JPG)

    ```
    실습 강의를 보고 따라하는 과정에서 생성한 test 내 여러 파일들과 압축 파일들을 전부 제거하였다.
    한번에 여러가지의 파일을 삭제하고 싶을 땐 
    -> rm -r test1.txt test2.txt 와 같이 
    rm -r * (* 자리에 제거할 파일명을 나열) 의 방법을 사용하면 보다 편리하다는 사실을 새롭게 알게 되었다.
    ```
  - test > OO_man.txt 파일 3개 생성

    ![00_man txt 파일 생성](https://user-images.githubusercontent.com/77660379/111018922-59b70d80-83ff-11eb-827f-f2a5b986ad14.JPG)


    ```
    1) touch less_man.txt (.txt파일 생성) => man less > less_man.txt (less에 대한 man 페이지를 less_man.txt 파일에 저장)
    2) touch more_man.txt => man more > more_man.txt (more에 대한 man 페이지를 more_man.txt 파일에 저장)
    3) touch mount_man.txt => man mount > mount_man.txt (mount에 대한 man 페이지를 mount_man.txt 파일에 저장)
    ```
  - tar 파일로 묶고, gzip 으로 압축

    ![압축](https://user-images.githubusercontent.com/77660379/111018936-6c314700-83ff-11eb-8d8a-4ee9af6180e0.JPG)


    ```
    상위 디렉토리로 이동하여 test에 접근하였다.
    (test 내에 less_man.txt, more_man.txt, mount_man.txt 파일이 존재하기 때문)
    터미널 창에 명령어는 tar zcvf gzip.tar.gz test 를 이용하였다.
    
    파일 압축 방법에는 2가지가 있는데,
    1) gzip 으로 압축할 경우 : tar zcvf gzip.tar.gz *
    2) bzip2 로 압축할 경우 : tar jcvf bzip2.tar.bz2 *
    의 명령어를 사용하면 된다.
    ```
  - TISTORY에 tar.gz 업로드

    ![firefox로 업로드](https://user-images.githubusercontent.com/77660379/111018954-7ce1bd00-83ff-11eb-8dbb-19919a4a6f43.JPG)

    ```
    vmware 가상 환경 내 firefox 웹 사이트로 tistory에 접근하였다.
    파일 첨부 과정은 drag-and-drop 으로 가능했고,
    실제 PC와 가상환경 내의 압축 폴더를 연동시키지 않아도 업로드 가능하다는 점에서 편리했다.
    ```

## 2. 실습과제 Review
* ### **새로 배운 내용**
```
1. Linux리눅스
    => 컴퓨터 운영체제 or 커널

2. VMware가상머신 (맥 os의 경우 VirtualBox)
    => PC 1대만으로 여러 대의 PC를 운영하는 것처럼 만드는 방법
       컴퓨터 1대에 실무와 비슷한 네트워크 환경 구성
       운영체제의 특정 시점을 저장하는 스냅숏 기능
       여러 개의 하드웨어를 장착하여 테스트 가능
       현재 상태를 저장했다 추후에 이어서 작업 가능 (Suspend 기능)
```

* ### **문제가 발생하거나 고민한 내용 + 해결 과정**
```
1. 문제발생 및 고민한 내용
  우분투 리눅스 Server(b) 설정
    => Why? Server(b)를 재부팅하는 과정에서 오류가 반복되는 상황 발생

2. 해결 과정
  Server(b)의 Edit virtual machine settings를 통해 설정을 맞추어줌
  (1) Memory 를 1GB로 줄여보았으나 해결되지 않음
  (2) Memory 를 2GB로 늘려주었더니 문제가 해결됨
  (3) 각 PC에 따라 가상머신의 하드웨어 설정이 달라질 수 있음을 깨달음 
```

* ### **참고할 만한 내용**
```
VMware를 사용하기에 적합한 경우
  => 실무와 비슷한 네트워크 환경을 구성하여 여러 대의 서버를 구축하려 할 때
  => 여러 가지 운영체제를 설치하여 학습하려 할 때
  => 새로운 시스템을 도입하기 전에 테스트해보려 할 때
```

* ### **회고 (+,-,!)**
```
1. 뿌듯했던 점 (+)
    => (1) Server(b) 재부팅 과정에서 오류가 발생했을 때 혼자의 힘으로 설정을 만져보며 해결해 낸 것
       (2) 리눅스 설정에 사용되는 문법들 암기한 것
       (3) LTS에 대한 지식을 미리 갖추고 있던 것

2. 보완할 점 (-)
    => C드라이브와 D드라이브를 구분하여 파일을 정리하면 효율성을 높일 수 있음
      -> 평소 드라이브의 위치에 따른 사용에 대해 고민해 본 적이 없어 C드라이브만 사용했었음 
      -> 이번 기회를 통해 중요치않게 생각하고 넘겼던 작은 부분들에서도 지식의 차이가 발생할 수 있음을 깨닫게 됨
      -> 컴퓨터를 다룰때 사소한 부분까지도 각 기능을 생각해보며 배우려는 자세를 갖춰야할 필요가 있음

3. 꼭 기억할 점 (!) 
    => PC 1대에서는 윈도우(호스트OS), 리눅스 서버, 리눅스 서버(b), 클라이언트 이렇게 총 4개의 운영체제가 가동됨
```