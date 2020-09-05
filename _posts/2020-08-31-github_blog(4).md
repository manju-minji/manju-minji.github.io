---
title: "Github 블로그 만들기(4) - 댓글 기능"
comments: true
classes: wide
categories:
  - github blog
tags:
  - github
  - disqus
  - 댓글
show_date: true
last_modified_at: 2020-09-05
---

### 블로그에 댓글 기능 추가하기

블로그에 댓글 기능이 없다면...너무 블로그가 황량하겠죠..? 소통의 일방통행이랄까..?

그래서 댓글 기능을 추가해보려고 합니다.

__Disqus__ 는 소셜 댓글 서비스의 하나입니다. 그래서 disqus를 이용하면 facebook, google, disqus 계정 등을 이용해서 댓글을 달 수 있습니다.

개인적으로 댓글 기능을 구현 할 필요 없이, 간단하게 댓글 기능을 추가 할 수 있어 좋습니다~!

## 구현

1. [Disqus 사이트](https://disqus.com/)에 접속합니다.

2. 계정이 없다면 회원 가입을 진행하고, 있다면 바로 __GET STARTED__ 를 클릭합니다.

   <img src='http://drive.google.com/uc?export=view&id=1yYHdn17ijKLeZVUx3VB0fktkWwqTnXkR' style="zoom: 33%;" />

3. __I want to install Disqus on my site__ 클릭 

   <img src='http://drive.google.com/uc?export=view&id=1MMo_eTnEEkMiQvngLAi0vdMruyLYwZwD' style="zoom:33%;" />

4. website name, category, language 항목을 작성 해 줍니다.(언어에 한국어가 없어요...ㅠ)

   <img src='http://drive.google.com/uc?export=view&id=1iOsTzg3NiB68Do-9PYwg5hfDsgkbRfoq' style="zoom: 33%;" />

5. 그 다음으로 넘어가면 어떤 서비스를 이용할 지 나오는데, 제일 밑에 내려가면 __Basic__ 이 있습니다. 이건 공짜에요. 이걸 선택하고 다음으로 넘어갑니다.

   <img src='http://drive.google.com/uc?export=view&id=17R_3BoBIt3IPSX4dwVBtdKrY5Scha4Qn' style="zoom:33%;" />

6. 어디에 설치 할 지 고르는 항목이 나옵니다. Jekyll을 이용하여 블로그를 만들었으므로 __Jekyll__ 을 선택합니다.

   <img src='http://drive.google.com/uc?export=view&id=1mdF-hEjb_ceRGqYg_bmOwKe7woPb8VYI' style="zoom:33%;" />

7. 그 후에 기타 설정 후 하단의 Complete Setup을 눌러줍니다.(이미지가 짤렸군요...)

   <img src='http://drive.google.com/uc?export=view&id=1X3n-69tUMu3PbzLoI2qiBdLxOdh-b8RO' style="zoom:33%;" />

8. 그 후에 Settings에 들어가면 __Shortname__ 을 확인 할 수 있습니다.

   <img src='http://drive.google.com/uc?export=view&id=1hIA5ToKhbJgtEzFPv2_zo3blShbJGiPb' style="zoom:33%;" />

9. _config.yml에 들어가서 comments의 항목에 위의 shortname을 추가 해 줍니다.

   <img src='http://drive.google.com/uc?export=view&id=1asg-ckZ7eS-ENKuVCghVsdZf4Hq9WgAp' />

   * 만약 _config.yml에 comments 항목이 없다면 직접 코드를 추가해주셔야 해요.(minimal-misktakes 테마 너무 좋다...다 되어 있어서...ㅎ) 그건 [블로그 주소](https://recoveryman.tistory.com/391) 여기서 보시는 게 좋을 듯.

10. 댓글 기능을 이용하고자 하는 게시물의 상단에 comments:true를 넣어주면, 댓글 기능을 이용할 수 있습니다.

    <img src='http://drive.google.com/uc?export=view&id=1ZGkOY1VBmObeNAyQQFYaYOGYuZ8IigTE' style="zoom:50%;" />

11. 완성 따란!!