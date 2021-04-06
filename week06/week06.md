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

- **mdadm 오류**

    ![sdc1 입력 오류](https://user-images.githubusercontent.com/77660379/113741813-fb9af300-973c-11eb-8c11-dabf22d6c928.JPG)

    ![sdb1 까지도 오류](https://user-images.githubusercontent.com/77660379/113741965-19685800-973d-11eb-855e-6aa119b1a635.JPG)

    ![초기화](https://user-images.githubusercontent.com/77660379/113742050-2e44eb80-973d-11eb-8657-f4c289486101.JPG)

    ![초기화후디스크](https://user-images.githubusercontent.com/77660379/113742107-3d2b9e00-973d-11eb-8c19-5942655b922d.JPG)

    ![sdc1 입력 오류 해결](https://user-images.githubusercontent.com/77660379/113742174-4c125080-973d-11eb-9889-12e0102fbbb2.JPG)

    ![전부 해결완료](https://user-images.githubusercontent.com/77660379/113742204-57657c00-973d-11eb-8aa3-6243bfe53376.JPG)

    ```
    문제발생 및 고민한 내용 : mdadm 을 이용한 RAID 생성 오류

    해결 과정 : 'You haven't given enough devices (real or missing) to create this array'라는 오류 문구 발생
               -> 한참을 고민했으나 오류가 무엇인지 찾지 못함
               -> 다시 한번 RAID 생성 구문을 터미널 창에 입력
               -> 오류 없이 실행됨으로 해결 완료
               -> 오류가 발생할 수 밖에 없었던 이유를 찾음
               -> * /dev/sdb1 /dev/sdc1 구문에서 sdb1 과 /dev 사이에 ' '(띄어쓰기)를 입력하지 않았었음
    ````

* ### **참고할 만한 내용**
```
리눅스 백업 관리 5주차 실습 전 서버 초기화를 위해 백업 진행

백업 종류
1) 완전 백업(Full Backup) : 모든 데이터를 통째로 한 번에 백업하는 방법
2) 증분 백업 (Incremental Backup) : 완전 백업한 이후에 변경된 데이터만을 주기적으로 따로따로 백업하는 방법
3) 차등 백업 (Differential Backup) : 완전 백업 후의 모든 데이터에 대해 백업하는 방법

백업/복구 명령어
1) 디렉터리 단위의 백업
    -> tar : 마운트 된 파일시스템 내에서 백업, 주로 사용
       cpip : 마운트된 파일시스템 내에서 백업
2) 파일시스템 단위의 백업 : dump/restore
3) 디스크 단위의 백업 : dd (잘 사용하지 않음)

tar 명령어를 통한 백업
1. su - // root 계정으로 변경하여 시스템 파일도 건드릴 수 있게 함
2. tar cvpzf{저장될경로와이름.tgz}--exclude=/proc--exclude=/lost+found--exclude=/media --exclude=/mnt --exclude=/dev --exclude=/sys --exclude={저장될경로와이름.tgz}/      
    // 제외할 폴더는 --exclude 옵션을 사용
     // c:새로운 파일 생성, v: 진행목록을 표시, p:파일 권한 정보를 기억, z:gzip으로 압축, f:파일이름 설정
     // 맨뒤에 /는, /에서부터 백업 (=최상단)

주기적인 백업 실행
crontab -e
0.4***/root/backup.sh1>/dev/nukk 2>/dev/null // 오전 4시에 실행

앞으로 실습을 진행하면서 백업은 필수사항이 될 것 같아 주기적인 자동 백업 방법을 추가적으로 알아보았다. 아직 리눅스에 대한 이해가 더 필요하기에 자동 백업을 실행시켜놨다가 괜히 문제가 발생할 수도 있을 것 같아 아직 시험해 보지는 않았다.
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