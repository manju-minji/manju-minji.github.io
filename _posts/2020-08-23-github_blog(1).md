---
title: "Github 블로그 만들기(1)"
comments: true
categories:
  - github blog
tags:
  - github
show_date: true
last_modified_at: 2020-08-31
---

### 왜 github 블로그를 만들게 되었는가?

github로 블로그를 만들 수 있다는 사실을 알기 전인 코딩 초창기에는 네이버 블로그에 알고리즘 문제 풀이 등을 업로드 하고는 했다.

그러다가 github 블로그를 만들 수 있다는 사실을 알게 되었고, 내가 직접 customize도 하고 github도 이용해서 블로그를 꾸려나간다는 사실이 너무 매력적이였다.

나만의  정적인 웹사이트라니...!

그리고 무엇보다도 뭔가 __간지__ 가 났다....ㅎㅎ...헷

github에 대해서 잘 모르는 사람이 github와 친숙해지기 위해서 블로그를 만들어 보는 것도 나쁘지 않을 듯 하다.

---

### 만드는 과정

1. 본인의 github 계정에 새로운 repository를 만든다.

   * 이때, repository의 이름은 __[본인아이디].github.io__ 로 설정해야 한다.

   * __Initialize this repository with a README__ 를 체크하여 신속한 작업을 돕는다.

     ![](http://drive.google.com/uc?export=view&id=1ArsOBLj74F_A_EbCGYeKIYx5I1JOqPCb)

   * 제대로 생성되었다면

     * setting의 하단에 보면 나오는 링크를 누르거나

       ![](http://drive.google.com/uc?export=view&id=1GT7Qhl36auScMTe_r3hVg8BZV-C-9rmG)

       ![](http://drive.google.com/uc?export=view&id=1PtB8plR1ch8blEsDz9NUCZza_Z8ccOKH)

     * 주소창에 [본인아이디].github.io를 쳤을 때 블로그가 나온다.

     * 단, 생성에 약간의 시간이 필요할 수도 있으니 생성 후 바로 주소로 들어갔을 때 안나온다고 좌절하지 말자.

2. 내 컴퓨터에 다운 받기

   * 이제 내 컴퓨터에서 블로그에 대한 설정을 수정하고, 글을 게시하고 관리하기 위해 다운을 받아야한다.

     ​	![](http://drive.google.com/uc?export=view&id=1DwrAlrrQKwqrfDH1VXaW84vx8q52fif4)

      1. 위의 이미지를 보면 주소가 나온다. 이 주소를 복사한다.

      2. terminal이나 cmd, git bash 등을 켜서 repository를 저장할 폴더로 이동한다.

         `$ cd 저장할 폴더 주소`

     	3. git clone을 통해 repository를 가져온다.

         `$ git clone 복사한주소`

         * 만약에 git 명령어가 작동하지 않는다면 git을 설치해야 하는데...이건 직접 각자의 OS에 맞게 검색해보자!

