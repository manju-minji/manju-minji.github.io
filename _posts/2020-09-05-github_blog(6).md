---
title: "Github 블로그 만들기(6) - google analytics"
comments: true
classes: wide
categories:
  - github blog
tags:
  - github
  - google analytics
show_date: true
last_modified_at: 2020-09-05
---

## google analytics란?

지난 게시글에서 사용한 Google Search Console을 통해서 구글 검색을 통해 내 블로그 방문자 정보를 확인 할 수 있긴하다.

하지만 google analytics를 통하면 구글 뿐만 아니라 블로그에 방문하는 모든 방문자의 정보를 확인 할 수 있다.

방문자들이 네이버 혹은 다음의 검색, 타사이트 추천, 직접 입력 등 무엇을 통해 블로그에 방문 했는지 도 알 수 있고, 이 외에도 방문자의 위치, 네트워크, 사용 기기 등의 정보도 확인할 수 있다. 

## google analytics 등록

1. [google analytics 사이트](https://analytics.google.com/analytics/web/provision/?hl=ko&pli=1#/provision) 에 접속한다.

2. 측정 시작을 누른다.

   <img src='http://drive.google.com/uc?export=view&id=1b4SqfFUXQcvu17KhOaNhPwfBJSiEfcMO' style="zoom:50%;" />

3. 내 구글 계정을 적어 준다.

   <img src='http://drive.google.com/uc?export=view&id=1FQIwZpekE3-EbvidFAtEk5xVP5zme5SB' style="zoom:50%;" />

4. 측정 하려는 대상 __웹__ 을 선택하고 다음으로 넘어간다.

   <img src='http://drive.google.com/uc?export=view&id=1QRqaRMNZPpMFS5PV68LSp--vfsf6EYfp' style="zoom:50%;" />

5. 내 블로그 주소를 입력하고 다른 세부 속성들을 설정한다.

   <img src='http://drive.google.com/uc?export=view&id=1KLtrryOw7i0YGRCSO1feneRWSOUC7mD4' style="zoom:50%;" />

6. _config.yml의 analytics 부분에 추적 ID를 넣어준다.

   <img src='http://drive.google.com/uc?export=view&id=1F15cT1Nghpnv_kbQiGcI2AP2yeqgyLXB' style="zoom:67%;" />

   <img src='http://drive.google.com/uc?export=view&id=18ZsROKPH0qKfY9ZA6FH_vuexMtI9j3q-' />

   * minimal-mistakes 테마를 추천한 이유가 이런식으로 _config.yml을 조금만 수정하면 여러 기능들을 쓸 수 있도록 잘 되어 있어서다.
   * 만약에 _config.yml에 저런 항목이 없다면...아래의 범용 사이트 태그에 있는 코드를 직접 추가해 줘야 한다.  이 방법은 [이 블로그](https://jybaek.github.io/dev/2016/07/04/use-google-analytics/)를 보는게 좋을 것 같다.

7. git push를 통해 _config.yml을 업데이트하고, google analytics에 들어가서 확인해보면 된다.