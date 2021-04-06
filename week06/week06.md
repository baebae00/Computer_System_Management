# 20200994 배서은
**컴퓨터시스템관리 6주차 실습일지**

---
#### 6주차에는 
1. RAID 와 LVM 을 직접 구현 및 작동 방식 설명
2. 쿼터의 개념 이해, 수정
---

## 1. 실습과제 결과

* ### **Server(b)에 LVM 설정**
  
* ### **하드디스크 2개 추가(2GB, 3GB) / LV 4개 설정(1GB, 1GB, 2GB, 1GB)** <br>

  - server 초기화 후 하드디스크 2개 준비 (2GB, 3GB)

    ![1](https://user-images.githubusercontent.com/77660379/113737105-b379d180-9738-11eb-8fa2-24f7a1061e56.JPG)

  - 물리적인 볼륨(PV) 생성

    ![2 물리적인 볼륨(PV) 생성](https://user-images.githubusercontent.com/77660379/113737191-c68ca180-9738-11eb-98ca-af04194b89b2.JPG)
    
  - 물리볼륨을 묶어 볼륨그룹(VG) 생성

    ![3 물리볼륨을 묶어 볼륨그룹(VG) 생성](https://user-images.githubusercontent.com/77660379/113737279-dc01cb80-9738-11eb-9c2f-03fb03c3d23b.JPG)

  - 논리볼륨(LV) 생성 (1GB, 1GB, 2GB, 1GB)

    ![4 논리볼륨(LV) 생성](https://user-images.githubusercontent.com/77660379/113737338-e754f700-9738-11eb-9040-76b575147de5.JPG)

  - 각 논리볼륨에 파일시스템 생성

    ![5 각 논리볼륨에 파일시스템 생성](https://user-images.githubusercontent.com/77660379/113737387-f471e600-9738-11eb-8f43-b25c4bcd4f93.JPG)

  - 논리볼륨 마운트

    ![6 논리볼륨 마운트](https://user-images.githubusercontent.com/77660379/113737481-06538900-9739-11eb-9b79-7ba4967816a7.JPG)

  - 부팅시 자동 마운트 설정

    ![7 부팅시 자동 마운트 설정](https://user-images.githubusercontent.com/77660379/113737531-12d7e180-9739-11eb-9954-6dad596e87b5.JPG)

  - LV 상태 출력

    ![8-1](https://user-images.githubusercontent.com/77660379/113737595-21be9400-9739-11eb-9c7b-a7465415b119.JPG)

    ![8-2](https://user-images.githubusercontent.com/77660379/113737647-300cb000-9739-11eb-8a71-a41481917a94.JPG)

    ![8-3](https://user-images.githubusercontent.com/77660379/113737722-40bd2600-9739-11eb-9a7e-f17190f19016.JPG)

    ![8-4](https://user-images.githubusercontent.com/77660379/113737770-4ca8e800-9739-11eb-9224-7030c99e7352.JPG)


## 2. 실습과제 Review

* ### **새로 배운 내용**
```
1. RAID 1+0
    => RAID 1으로 구성한 디스크를 다시 RAID 0 로 구성

       데이터의 신뢰성(안전성)과 성능(속도)을 동시에 확보

       공간효율은 50%


2. LVM, Logical Volume Manage
    => 논리적 볼륨을 효율적이고 유연하게 관리하기 위한 커널의 한 부분이자 프로그램

       용량 조절, 크기 조절, 편의에 따른 장치 이름 지정, 디스크 스트라이핑, 미러 볼륨 제공

       전통적인 시스템 vs LVM 기반 시스템
         -> PV, Physical Volume
             => LVM에서 사용할 수 있는 블록 장치 전체 또는 블록 장치를 이루고 있는 파티션
            PE, Physical Extent
             => PV를 구성하는 일정한 크기의 블록 (LVM2 에서 기본크기는 4MB)
            VG, Volume Group
             => PV들의 집합으로 LV를 할당할 수 있는 공간
            LV, Logical Volume
             => Linear LV / Striped LV / Mirrored LV
            LE, Logical Extent
             => LV를 구성하는 일정한 크기의 블록
        
        여러 개의 HDD를 합쳐서 한 개의 파일 시스템으로 사용, 필요시 다시 논리적으로 나눌 수 있음


3. Quota 쿼터
     => 파일 시스템마다 사용자나 그룹이 생성할 수 있는 파일의 용량 및 개수를 제한하는 것

        쿼터용 파일시스템 설정 > 쿼터 DB 생성 > 개인별 쿼터 설정
```

* ### **문제가 발생하거나 고민한 내용 + 해결 과정**

- **sdc1 오류**

    ![sdc1 입력 오류 해결](https://user-images.githubusercontent.com/77660379/113742174-4c125080-973d-11eb-9889-12e0102fbbb2.JPG)

    ![sdc1 입력 오류](https://user-images.githubusercontent.com/77660379/113741813-fb9af300-973c-11eb-8c11-dabf22d6c928.JPG)

    ```
    문제발생 및 고민한 내용 : sdc1 파티션 생성 오류

    해결 과정 : sdc1 생성시 설정을 잘못한 상태에서 저장해버림
               -> sdc1을 영구적으로 삭제한 후 sdc1을 새로 만들기로 결정함
               -> fdisk /dev/sdc > d > w 의 과정을 거쳐 파티션을 삭제해줌
               -> ls -l /dev/sd* 명령어를 통해 디스크 정보를 확인한 결과 sdc1이 삭제됨
               -> 강의 내용과 같은 sdc1을 새롭게 생성해줌
    ````

* ### **참고할 만한 내용**

[fdisk로 파티션 삭제하기](http://www.lionheart.pe.kr/index.php?mid=board_uFoa63&order_type=desc&page=3&document_srl=2113&sort_index=title)
```
Command(m for hep) : p
  => 현재 파티션 정보 확인

Command(m for hep) : d
  => 파티션 삭제 (번호 고르기 sdb 뒤에 나오는 숫자로 확인)

Command(m for hep) : n
  => 파티션을 전부 삭제한 후 n을 쳐서 새로운 파티션 생성

Command(m for hep) : l
  => 선택할 수 있는 파티션 타입 확인(ex. Linux, fat 등등)

Command(m for hep) : t
  => 파티션 넘버를 선택한 후 위에서 기억한 파티션 타입 입력

Command(m for hep) : w
  => 저장하고 나옴
```

* ### **회고 (+,-,!)**
```
1. 뿌듯했던 점 (+)
    => vi 대신 gedit을 주로 사용
          -> vi 를 이용할 때 i를 이용해 쓰기모드로 바꿔줘야하거나 다음 입력으로 넘어갈 때 ESC버튼을 눌러야하는 등 굉장히 번거러움
             이러한 명령어를 제대로 사용하지 않을 경우 이상한 문자가 적히거나 커서가 안움직이는 등의 문제 발생
             강의에서 vi 로 파일 내용을 수정할때마다 gedit 명령어를 사용했음 
             리눅스에 대한 이해가 쌓일 수록 보다 나한테 맞고 보다 쉬운 방법을 하나씩 스스로 활용할 수 있어진다는 사실에 뿌듯했음

2. 보완할 점 (-)
    => 터미널 창에 명령어를 입력할 때 띄어쓰기 하나도 중요하다는 사실 자각할 것
      -> 특히 긴 문장을 입력할 때 문자 하나라도, 혹은 띄어쓰기 하나라도 한번 더 검토하기
         띄어쓰기 같은 작은 부분 때문에 오류가 생길 것이라 생각해보지 않아서 한참 헤맸음

3. 꼭 기억할 점 (!) 
    => RAID 구성할 때 먼저 우분투의 Edit virtual machine settings에서 하드디스크를 추가 생성해줘야 함
       이 부분에 대한 이해가 충분하지 못해서 Server(b)에 파티션을  생성할 때 바로 fdisk /dev/sd* 의 명령어를 사용했더니 파티션을 찾을 수 없다는 오류가 발생했음
       sdb와 sdc 를 생성하고 싶다면 환경 설정에서 하드디스크 2개를 미리 추가해 준 후 가상머신 실행하기