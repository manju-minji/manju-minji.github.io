---
title: "Github 블로그 만들기(2) - 테마 설정, 테마 추천"
comments: true
categories:
  - github blog
tags:
  - github
  - jekyll
show_date: true
last_modified_at: 2020-08-31
---

### 테마 넣기 - Jekyll

만든 github page를 일일히 내가 예쁘고 실용적으로 사용 가능하게 꾸며나간다는 것은 매우 많은 시간과, 노력을 요할 것이다. ~~그렇다면 굳이 page를 안 만들었을 듯~~

하지만 여기에 Jekyll을 결합한다면 이러한 나의 고생을 덜면서 꽤 훌륭한 모양새를 갖춘 블로그를 만들 수 있다.



1. 테마 고르기

   * Jekyll에는 아래와 같이 여러가지 테마들이 있다.

   ![](http://drive.google.com/uc?export=view&id=1U8SYUjQToccwWYmKx6nl9_pBpWlvJogQ)

   * 이 테마를 사용하기 전에...여러 테마들을 사용해 봤는데 이 테마가 제일 좋은 것 같다.

     이 테마의 이름은 '[minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)'이다.

     * 왜 이 테마가 좋냐?
       * 블로그를 customize하기 좋게 만들어 놨다. 정말.
       * 게다가 잘 모를까봐 넣어놓은 예제 파일들도 너무 좋고, 설명도 너무 잘 되어 있다.

2. 테마 다운 받아서 repository에 넣기

   ![](http://drive.google.com/uc?export=view&id=1wE1dYixhIL8huY1Ioyb-z0qYwv2Ydomf)

   * download zip을 해서, 이전 포스팅의 clone을 통해 생긴 내 블로그 파일에다가 넣고 압축을 풀어준다.

3. customize하기

   _config.yml에 들어가면 블로그 이름부터 하나하나 customize 할 수 있다. 

   테마마다 다를 수 있음을 주의하자.

   minimal-mistakes 테마의 경우 'Quick Start Guide'라는 것이 있다. 이것을 보고 차근차근 따라하면 좋을 듯 하다.

   질문이 있다면 댓글로

   {: .notice--warning}

4. 적용 확인하기

   * 우리가 변경한 내용들을 github에 올려줘야한다.

     `$ git add .`

     `$ git commit -m "테마 추가"`

     `$ git pull`

   * 잠시 뒤에 내 블로그 주소로 들어가보면 테마가 적용된 것을 확인 할 수 있다.