---
title: "portable linux - persistent live usb(비휘발성 live linux)"
comments: true
categories:
  - life
tags:
  - linux
  - ubuntu
show_date: true
last_modified_at: 2020-09-10
toc: true
toc_sticky: true
toc_label: 목차
---

> 들고 다닐 수 있는 리눅스 만들기!



리눅스는 특이하게 usb에 설치해서도 사용이 가능한데요.



그래서 리눅스를 연습하고 싶은데 하드 디스크를 잘못 건드릴까 무섭거나(잘못 건드려서 컴퓨터 맛간 사람들 여럿 봤습니다...), 가상 머신(VMware 같은...)의 사용이 답답/불편하거나,여러 컴퓨터를 옮겨 다니면서 작업하거나 하는 등의 사람들에게 유용한 방법을 하나 알려드리려고 합니다.



바로 __persistent 하게 live usb__ 를 만드는 것인데요.



말 그대로 비휘발성으로 개인의 데이터를 저장하면서도 usb를 이용해 linux를 사용할 수 있다는 것이에요!!



### 준비

* 4GB 이상의 아무것도 없는 USB 준비하기



### step1. ubuntu 다운 받기

* <a href="https://releases.ubuntu.com/focal/" target="_blank">https://releases.ubuntu.com/focal/</a>

  <img src='http://drive.google.com/uc?export=view&id=1YXplIJFNhAQrNMqRYQwDvkJdY-TlYsXA' style="zoom:33%;" />

​	위의 링크를 통해서 Desktop image 파일을 다운 받아도 되지만 느릴 수 있으므로(밤에 받으면 진짜 느려요....아침에 받는 걸 강추)

​	카카오와 KAIST에서 제공하는 미러링 서버를 이용하는 것도 좋습니다.

* <a href="http://mirror.kakao.com" target="_blank">kakao</a>
* <a href="http://ftp.kaist.ac.kr" target="_blank">KAIST</a>



<div class="notice--waring">
    <strong>주의 사항</strong> - 18.04 버전은 persistent하게 만들어지지 않아요.<br>
    처음에  20.04 버전이 나오지 않은 상황에서 18.04를 이용해서 persistent하게 만들려고 갖은 노력을 했는데...안되더라고요. 그냥 그 버전이 안되는거였어요.(열심히 구글링해서 안되는 것을 깨달음)<br>
    그래서 <strong>20.04</strong>버전을 사용하셔야 데이터가 저장되는 ubuntu usb를 가질 수 있어요!
</div>



### step2. rufus 다운 받기

<a href="https://rufus.ie/" target="_blank">rufus 다운 링크</a>

rufus라는 응용 프로그램을 이용해서 ubuntu usb를 만들어 줄 겁니다.

### step3. usb 만들기

1. rufus를 실행 후 다운 받은 iso 파일을 넣어주고, 영구적인 파티션 크기를 지정해 줍니다.

<img src='http://drive.google.com/uc?export=view&id=1v1jIfQ27m73AfIDr6TqoKJ5m8RfJoEH_' style="zoom:33%;float: center"/>

​	<img src='http://drive.google.com/uc?export=view&id=1A_KhQsQivms7-aHpDD0sif2el_i1r95U' style="zoom:33%;" />

2. 이런 창이 뜨면 제대로 만들어진다는 거예요.(이런 창 안뜨면 정상적으로 작동하지 않음.)

   <img src='http://drive.google.com/uc?export=view&id=1hjR-ba9T56vP4bEHhG6o94q6U5_MPi9F' style="zoom:33%;" />

3. 데이터 다 삭제된다는 창도 나와요.

   <img src='http://drive.google.com/uc?export=view&id=1sC2WbizPbWUIGdrVSMXoSEHiyWaisvqq' style="zoom:33%;" />

4. 그리고 시작을 누르면 이렇게 됩니다.

   <img src='http://drive.google.com/uc?export=view&id=17But9Oz7iVMDnC6g6a62GFqNSAqWK5ja' style="zoom:33%;" />

5. 완료되었으면, 정상 설치 및 작동이 되었는지 컴퓨터를 종료한 뒤에 다시 부팅 해 줍니다. 이때, 바이오스 모드(bios mode)로 진입을 해서 usb로 부팅이 되도록 설정을 해줘야 합니다.

   * 바이오스 모드 진입 방법은 사용하는 제품마다 달라요. 삼성 노트북의 경우 f2를 누르면 됩니다.
   * 부팅이 시작 될 때 f2(삼성 노트북의 경우)를 계속 누르고 있으면 바이오스 모드로 들어가져요.

6. Boot 메뉴에서 Boot Device Priority를 들어갑니다.

   <img src='http://drive.google.com/uc?export=view&id=1n2l1L_957sltIde_9vpPKNlit5KS7uEt' style="zoom: 33%;" />

7. usb를 부팅 우선 순위로 설정해주고, save를 누르면 컴퓨터가 다시 시작 됩니다.

   <img src='http://drive.google.com/uc?export=view&id=1idedLTL8tVUzOr-J-HRaO2wezNA9LaOC' style="zoom:33%;" />

8. 다시 시작 후에는 우분투가 시작되고,(처음에는 검은 화면 나오는데 당황하지 마세요...) 우분투 화면이 나오면 여기서 Try Ubuntu를 눌러줍니다.

   <img src='http://drive.google.com/uc?export=view&id=1XB5WU3VJaNvmAuejeWP7aiYJuEGwuW5x' style="zoom:33%;" />

9. 짜잔!

   <img src='http://drive.google.com/uc?export=view&id=1XojB_ppXkxaNo5TQNXIJWueTOIgayiHt' style="zoom:33%;" />

10. 아까 설정한 용량 만큼 공간도 있군요!

    <img src='http://drive.google.com/uc?export=view&id=1RICg6wmwLOsOJi2u8utC4r3RCCUrBC0I' style="zoom:33%;" />

11. 그리고 다시 껐다가 켜도 내가 설정한 정보, 내가 저장한 데이터들이 그대로 남아있는 것을 보실 수 있을겁니다~!



{% include default_mention.html %}
