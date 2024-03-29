# 20200994 배서은
**컴퓨터시스템관리 8주차 실습일지**

---
#### 8주차에는 
1. week02 ~ 07 까지의 내용 복습 및 어려웠던 부분 2가지 골라 스스로 문제를 만들고 실습
2. week03 - 사용자 계정 생성, 그룹 설정에서부터 공동 편집 및 관리를 위한 링크 파일 생성하기
3. week06 - 사용자 계정 생성 후 Quota 로 사용자별 공간 할당해보기
---

## 1. 실습과제 결과

* ### *#1* **사용자 계정 생성, 그룹 설정에서부터 공동 편집 및 관리를 위한 링크 파일 생성하기**
  
* #### **cs, it, ss-univ 그룹을 생성 및 그룹에 계정 등록하기 & 공동 편집 및 관리를 위한 링크 파일을 생성하고 수정하기** <br>
    
  * 사용자 계정 생성 및 관리
    <br>

    cs, it, ss-univ 그룹을 생성한 후 cs-01, cs-02 계정은 cs, ss-univ 그룹에, it-01, it-02 계정은 it 그룹에 등록했다.
    <br><br>

  * 공동 편집 및 관리를 위한 링크 파일 생성
    <br>
    
    이후 공동 편집을 위한 링크 파일을 생성하고 파일을 수정할 수 있는 계정을 설정하는 실습을 진행하였다.<br>
    **그룹별 심볼릭 링크 파일과 원본 파일 백업을 위한 하드 링크 파일을 생성**해 주었다. it-01 보조그룹으로 ss-univ 를 추가하며 여러 계정으로 파일을 수정하고 확인하는 과정을 거쳐 실습을 마무리 하였다. (#2와 같이 변형해 새로 문제를 만들고 싶어 고민했다. 그러나 3주차 실습이 가장 어렵게 느껴진만큼 기존 실습 강의안을 올바르게 따라가며 복습하는 것에 의의를 두기로 했다.)
    <br><br>

  * 실행 결과

    - 공동 편집을 위한 원본 파일 생성 /board.txt

        ![01](https://user-images.githubusercontent.com/77660379/116006783-bb49d900-a647-11eb-8bbc-ad4d82e3424d.JPG)

    - 그룹별 접근 (심볼릭) 링크 파일 생성 / cs-board, it-B

        ![02](https://user-images.githubusercontent.com/77660379/116006804-cb61b880-a647-11eb-91a5-dafd61d08546.JPG)

    - 원본 파일 백업을 위한 (하드) 링크 파일 생성 / board.txt.bak
      <br>원본 파일인 board.txt를 제거했을 때 그 내용을 다시 복구하기 위해 미리 만들어놓는 백업 파일이다. 

        ![03](https://user-images.githubusercontent.com/77660379/116006812-d4528a00-a647-11eb-80f6-cacbf1a8b371.JPG)

    - cs-01 계정으로 cs-board 파일 수정
      <br>cs-01 계정으로 cs-board 파일을 수정하면 공동 편집을 위한 원본 파일인 board.txt의 내용이 수정된다.

        ![04](https://user-images.githubusercontent.com/77660379/116006824-e16f7900-a647-11eb-9506-753cafe478a5.JPG)

        ![05](https://user-images.githubusercontent.com/77660379/116006832-eb917780-a647-11eb-83d0-012ea503cd75.JPG)
    
    - it-01, it-02 보조그룹 ss-univ 설정

        ![06](https://user-images.githubusercontent.com/77660379/116006846-f77d3980-a647-11eb-90c0-dd4a23f96519.JPG)

    - it-02 계정으로 it-B 파일 수정
      <br>위 과정과 같이 it-02 계정으로 it-B 파일을 수정하면 공동 편집을 위한 원본 파일인 board.txt의 내용이 수정된다.

        ![07](https://user-images.githubusercontent.com/77660379/116006865-0368fb80-a648-11eb-8268-6bb28e1b1783.JPG)

        ![08](https://user-images.githubusercontent.com/77660379/116006869-07951900-a648-11eb-8a42-2328cb624771.JPG)

    - 원본 파일인 board.txt 파일을 삭제하고 ls -l 해보니 링크 파일에 문제가 생긴 것을 알 수 있다.

        ![09](https://user-images.githubusercontent.com/77660379/116006883-1a0f5280-a648-11eb-8623-9f6dbc17957a.JPG)

    - 원본 파일인 board.txt 파일을 백업한 결과 링크 파일및 링크 파일과 원본 파일의 연결이 복구된 것을 확인할 수 있다.

        ![10](https://user-images.githubusercontent.com/77660379/116006898-25627e00-a648-11eb-9ef1-676fe4a407a5.JPG)
<br><br><br>

* ### *#2* **사용자 계정 생성 후 Quota 로 사용자별 공간 할당해보기**
  
* #### **ryan(라이언), apeach(어피치), con(콘) 각각이 사용할 수 있는 파일의 용량 제한 by Quota** <br>
    
  * 새로운 HDD 인식
    <br>

    먼저 server(b)를 초기화한 후 10GB의 새로운 HDD를 장착했다. 이후 파티션, 파일시스템을 차례로 생성한 후 부팅시 자동 마운트 되도록 설정해 주었다.
    <br><br>

  * 쿼터 설정
    <br>
    
    본격적으로 사용자별 공간 할당 실습을 진행하였다.<br>
    우선 **라이언, 어피치, 콘 이렇게 세 명의 사용자를 생성해 주었으며 쿼터DB를 생성해 개인별 쿼터를 설정**해 주었다.
    <br><br>

  * 실행 결과

    - 사용자 계정 3개 생성 (라이언, 어피치, 콘)

        ![01](https://user-images.githubusercontent.com/77660379/116003379-b0d41300-a638-11eb-8c78-0fc4c2d27cf4.JPG)

    - /dev/sdb1 디렉터리 쿼터용으로 설정 후 /userHome 재마운트

        ![02](https://user-images.githubusercontent.com/77660379/116003390-c0535c00-a638-11eb-9ec4-aea2a802bc07.JPG)
    
    - 쿼터 설정

        ![03](https://user-images.githubusercontent.com/77660379/116003409-cea17800-a638-11eb-8153-b597d547f650.JPG)

     - 사용자별 공간 할당(라이언, 어피치, 콘 모두 15MB 공간을 각각 할당해주었다.)<br>
        실상 라이언에게 soft 10240KB, hard 15350KB 를 할당한 후 edquota -p 명령어를 사용해 어피치와 콘에게도 같은 양의 공간을 할당해 준 것

        ![04](https://user-images.githubusercontent.com/77660379/116003420-d8c37680-a638-11eb-873e-840485184c92.JPG)



## 2. 실습과제 Review

* ### **week01 ~ week07 복습**

 * **2주차**
    <br>
    *런레벨 변경*
    <br>
    ![img01](https://user-images.githubusercontent.com/77660379/116008304-ceac7280-a64e-11eb-86d2-8dab5fe474cd.JPG)

    *vi에디터*
    <br>
    ![img02](https://user-images.githubusercontent.com/77660379/116008330-f1d72200-a64e-11eb-8ab3-7ceae3291e8f.JPG)

    *파일 묶기와 압축*
    tar 파일 묶기 :  tar cvf ubuntu.tar*
    tar 파일로 묶고, gzip 으로 압축하기 : tar zcvf gzip.tar.gz*
    tar 파일로 묶고, bzip2 로 압축하기 : tar jcvf bzip2.tar.bz2*
    <br><br>

  * **4주차**
    <br>
    *X윈도우*
    유닉스 계열 운영체제에서 사용되는 윈도우 시스템
    디스플레이 장치에 창을 표시하며, 마우스와 키보드 등 입력장치의 상호작용을 관리해 GUI 환경 구현을 위한 기본적인 프레임워크 제공
    네트워크 프로토콜 기반의 클라이언트-서버 모델
    다양한 모습의 데스크톱 환경(KDE, GNOME, Xface 등)이 X윈도우를 기반으로 사용함
    <br><br>

 * **5주차**
    <br>
   *하드디스크 추가*
    <br>
    ![img03](https://user-images.githubusercontent.com/77660379/116008535-0f58bb80-a650-11eb-9eff-943ed5ac1f5e.JPG)

    1) 가장 먼저 설치한 디스크의 파티셔닝을 위해 fdisk
    2) 파티셔닝한 하드의 파일포맷 mkfs(파일시스템 생성)
    3) 해당 하드를 본격적으로 사용하기 위해 mount 해서 하드디스크 장치에 연결
    4) 부팅시 마운트한 내용을 유지하기 위해서 /etc/fstab 을 편집

    *RAID*
    <br>
    여러 개의 하드디스크를 하나의 하드디스크 처럼 사용하는 방식
    비용, 신뢰성, 성능 조절의 효과
    <br><br>

 * **7주차**
    <br>
    *Shell*
    사용자와 커널 사이에서 명령을 해석해 전달하는 기능
    자체 내에 프로그래밍 기능이 있어서 프로그램 작성 가능
    셸 프로그래밍 기능을 이용하면 여러 명령을 사용해 반복적으로 수행하는 작업을 하나의 프로그램으로 제작 가능(셸 프로그램을 셸 스크립트라고 부름)
    사용자의 환경 설정 가능
    <br><br><br>

* ### **문제가 발생하거나 고민한 내용 + 해결 과정**

- **remount 오류**

    장치 리마운트 과정에서 명령어를 입력했더니 자꾸만 오류가 났다. <br>

    ![오류01](https://user-images.githubusercontent.com/77660379/116006967-7b372600-a648-11eb-8f57-864695d6929c.JPG)

    <br>처음 오류가 발생하였을 때는 mount -options remount /userHome 명령어에서 문제가 생긴 줄 알고 options를 o로 변경해 보았다.(오류 해결을 위해 찾아본 사이트에서 제공한 방법) 그러나 오류는 해결되지 않았다. 따라서 상위 과정으로 거슬러 올라가 해결점을 찾고자 하였다.
    <br>

    ![오류01_1](https://user-images.githubusercontent.com/77660379/116006971-7ffbda00-a648-11eb-8b5b-2028f114ca04.JPG)

    <br>defaults, usrjquota=aquota.user,jqfmt=vfsv0 뮨장에서 vfsv()로 변경해보아도 해결되지 않았다. 결국 문제점을 찾아냈는데 **usrjquota에서 usr이 아닌 user로 입력했기 때문**이었다.(오타, 띄어쓰기의 중요성은 매주 실습 때 마다 느끼는 것 같다.) 그렇게 해결 완료되었다.
    <br>

    - [쿼터 관련 명령어와 옵션 참고](https://jhnyang.tistory.com/265)


* ### **참고할 만한 내용**

  * 리눅스 공간 할당

    ![img05](https://user-images.githubusercontent.com/77660379/116009016-28fb0280-a652-11eb-8202-f911bbc79779.JPG)

    [리눅스 공간 할당 개념잡기](https://ansan-survivor.tistory.com/45)

    하드디스크 추가하여 파티션을 마운트 하는 과정의 명령어와 그림을 함께 보면서 이해를 높였다. 정리해보자면,<br>
    **마운트**는 하드디스크와 커널을 붙여주는 작업이다. 즉 /root 아래 파일구조들이 만들어지는 것이며 그 공간 할당은 사용자가 필요한 만큼 자유롭게 할당 할 수 있다.<br>
    **PV**란 파티셔닝으로 나눠진 공간이다. sda1, sda2, sda3... 이라는 이름으로 등록하여 나눠진 구역들을 의미하는데 이는 물리적으로 내부에 선을 그은 것이기 때문에 이후에 확장 및 축소가 어렵다.<br>
    **LV**는 PV의 대안으로 등장했다. 물리적인 공간을 크게 할당하고 그 내부에서 논리적으로 선을 긋고, 필요시 지우고 다시 늘리고 줄이고 하는 작업을 편하게 만드는 방법이다.<br>
    **VG**는 LV를 논리적으로 자유롭게 쓰고 지울 수 있는 공간을 만드는 것이다. 즉 간단한 커맨드 라인으로 디렉터리를 만들고 지우고를 할 수 있어 관리가 아주 용이하게 된다.
    <br>

  * 셸의 변경, 개념, 기능 종류
    
    ![img04](https://user-images.githubusercontent.com/77660379/116008807-627f3e00-a651-11eb-9629-f6ddb3b7023c.JPG)

    [shell 이란?](https://jhnyang.tistory.com/57)

    셸은 커널과 사용자간의 다리역할을 하는 것, **사용자로부터 명령을 받아 그것을 해석하고 프로그램을 실행하는 역할**
    <br>쉽게 말해 Server의 검은 바탕의 글자만 있는 텍스트 모드 or X윈도우의 터미널처럼 명령어를 입력하는 환경을 말한다.
    <br><br>

* ### **회고 (+,-,!)**
```
1. 뿌듯했던 점 (+)
    => 어떤 방식으로 실습할지 고민을 많이 한 것
          -> 어떻게 하면 조금이라도 더 재미있게 실습할 수 있을까를 고민하느라 실습의 대부분의 시간을 보냈다. 고민을 하면서 강의안도 천천히 읽어보며 곱씹어보고 모르는 부분은 또 찾아보았는데 이 점이 복습에 많은 도움이 된 것 같다.
       
2. 보완할 점 (-)
    => 복습은 중요한 것
      -> 중간 대체 실습을 앞두고 지금까지 배운 내용들을 스스로 돌아보며 복습하는 시간이 주어져서 정말 다행이라는 생각이 들었다. 특히 3주차와 6주차는 강의를 100퍼센트 이해하고 넘어가지 못한 부분이 있었기 때문에 이번 실습이 더더욱 의미있었다.
      확실히 배운 내용을 다시 한번 스스로 정리해보니 당시에는 이게 정확히 무엇을 가리키는 지 헷갈렸던 부분도 확실하게 습득하고 넘어갈 수 있게 되었다. 결론은 중간 대체 실습이 나오기 전에 2주차부터 7주차까지 다시 한번 복습하는 시간을 가지면 좋을 것 같다.
 
3. 꼭 기억할 점 (!) 
    => 오타, 띄어쓰기 주의하기
         -> 리눅스를 통한 실습이 전부 명령어로 이루어지다 보니까 명령어 중 단어 하나, 혹은 띄어쓰기 한번에 오류가 자주 발생하는 것 같다. 때문에 큰 오류인지부터 의심하기 떄문에 항상 강의를 되돌려보며 어디서부터 잘못된건지 파악하느라 시간이 많이 걸린다. 그러나 매번 오류는 작은 데에 있었다. 때문에 더더욱 문자 하나라도 띄어쓰기 하나라도 한번에 제대로 입력하도록 주의해야겠다고 이번 실습에서도 다짐했다.