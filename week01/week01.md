# 20200994 배서은
**컴퓨터시스템관리 1주차 실습일지**

## 1. 실습과제 결과

* ### **가상머신과 3개의 리눅스 운영체제 설치**
  - VMware
    ![vmware](https://user-images.githubusercontent.com/77660379/109816988-b7678f00-7c74-11eb-8a46-ae8857d4be55.JPG)
  
  - Ubuntu Desktop
    ![ubuntu_desktop](https://user-images.githubusercontent.com/77660379/109817514-5be9d100-7c75-11eb-8279-ba6a14c3bb69.JPG)
    
  - Ubuntu Server
    ![ubuntu_server](https://user-images.githubusercontent.com/77660379/109817962-d74b8280-7c75-11eb-93bd-aa8096cf5ca8.JPG)
  
  - Kubuntu
    ![kubuntu](https://user-images.githubusercontent.com/77660379/109818045-eb8f7f80-7c75-11eb-91d8-6a59b79f5a3f.JPG)

* ### **관리자 설정**
  - Server 설정
    ```
    터미널 열기
    root 계정 활성화 (sudo su - root, passwd)
    root 계정으로 로그인 (sudo su)
    방화벽 설정 (ufw enable)
    한영변환 (키보드 레이아웃 한국어로 변경, shift + space)
    계정 로그아웃 (exit)
    해상도 변경 (1024x768)
    소프트웨어 자동 업데이트 해제
    ```
  - Server(b) 설정
    ```
    root 계정 활성화 (sudo su - root, passwd)
    재부팅 (reboot)
    방화벽 설정 (ufw enable)
    컴퓨터 종료 (halt -p)
    ```
  - Kubuntu 설정
    ```
    해상도 변경 (1024x768)
    ```

* ### **부팅 및 로그인 화면** <br>
    [부팅 및 로그인 화면 영상 URL](https://lsh424.tistory.com/37)

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

```

* ### **회고 (+,-,!)**
```
1. 뿌듯했던 점 (+)
    =>
2. 보완할 점 (-)
    =>
3. 꼭 기억할 점 (!) 
    =>
```



# 2. 번호 없는 리스트 작성
* 리스트1
  - 리스트2
    + 리스트3
    
# 3. 번호 있는 리스트 작성
1. 리스트1
2. 리스트2
3. 리스트3 

# 4. 이텔릭체(기울어진 글씨) 작성
*텍스트*

# 5. 굵은 글씨 작성
**텍스트**

# 6. 인용
> 인용1

> 인용2
>> 인용안의 인용

# 7. 수평선 넣기

---
  
# 8. 링크 달기
(1) 인라인 링크  

[블로그 주소](https://lsh424.tistory.com/)

(2) 참조 링크  

[블로그 주소][blog]

[blog]: https://lsh424.tistory.com/

# 9. 이미지 추가하기
![이탈리아 포지타노](https://user-images.githubusercontent.com/31477658/85016059-f962aa80-b1a3-11ea-8c91-dacba2666b78.jpeg)

### 이미지 사이즈 조절
<img src="https://user-images.githubusercontent.com/31477658/85016059-f962aa80-b1a3-11ea-8c91-dacba2666b78.jpeg"  width="700" height="370">

### 이미지 파일로 추가하기
<img src="Capri_Island.jpeg" width="700">

# 10. 코드블럭 추가하기

```swift
public struct CGSize {
  public var width: CGFloat
  public var heigth: CGFloat
  ...
}
```

# etc

**텍스트 굵게**  
~~텍스트 취소선~~

### [개행]  

스페이스바를 통한 문장개행  
스페이스바를 통한 문장개행  

br태그를 사용한 문장개행
<br>
<br>
br태그를 사용한 문장개행


### [체크박스]

다음과 같이 체크박스를 표현 할 수 있습니다. 
* [x] 체크박스
* [ ] 빈 체크박스
* [ ] 빈 체크박스

### [이모지 넣기]
❤️💜💙🤍

### [표 넣기]
|왼쪽 정렬|가운데 정렬|오른쪽 정렬| 
|:---|:---:|---:| 
|내용1|내용2|내용3| 
|내용1|내용2|내용3| 

<br>

### 부팅 및 로그인 화면 영상 URL
[부팅 및 로그인 화면](https://lsh424.tistory.com/37)