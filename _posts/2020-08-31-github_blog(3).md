---
title: "Github 블로그 만들기(3) - 로컬 개발 환경 구축"
comments: true
classes: wide
categories:
  - github blog
tags:
  - github
  - jekyll
  - ruby
show_date: true
last_modified_at: 2020-08-31
---

### 왜 하는 거야 이걸?

블로그의 아주 사소한 부분을 수정해서 그 결과를 보기 위해서라도 github에 commit pull 기다림....너무 귀찮다.

그래서 __바로바로__ 변동 사항을 localhost:4000으로 볼 수 있는 방법을 알려주고자 한다!

### 로컬 개발 환경 구축

1. 루비(Ruby) 설치하기

   * [루비 다운로드 링크](https://rubygems.org/pages/download) 로 이동해서 파일을 __다운__ 받자!

     * window는 zip 파일을 mac은 tgz 파일을 다운 받으면 된다.
     * 다운 후에는 압축을 푼다.

   * terminal이나 cmd창을 열어서 압축을 푼 위치로 이동 한 뒤 **ruby setup.rb을 실행**하여 다운로드한다.

     ```
     
     ```

     $ cd 압축푼위치

     $ sudo ruby setup.rb

     ```
     
     ```

   * `$ ruby --version`을 했을 때 현재 버전이 나오면 설치가 성공적으로 된 것이다.

2. jekyll bundler 설치하기

   * `$ gem install jekyll bundler` 명령어를 통해 jekyll bundler를 설치한다.

3. 확인해보기

   `$ cd 내컴퓨터의블로그repository`

   `$ bundle exec jekyll serve`

   * 위의 명령어들을 입력한 후에 

     ![](http://drive.google.com/uc?export=view&id=1_Jx6K82bWqyvim-h6L0OumYFrevYsx6x)

     와 같은 메세지가 뜨면 성공적으로 localhost:4000에 올라갔다는 뜻이다.

   * 주소창에 localhost:4000를 입력하면 내 블로그가 성공적으로 나오는 것을 확인 할 수 있다.

### 발생 가능한 오류

* __Gem::FilePermissionError__{: .notice--danger}

  ​	*	이 블로그에서 제시하는 방법을 따라하면 된다. [블로그 가기](https://jojoldu.tistory.com/288)

* __incompatible character encodings: ASCII-8BIT and UTF-8__{: .notice--danger}

  post의 이름 형식은 **년도-월-일-제목.형식**이여야 한다.

  이때, 제목이 영어가 아니라 한국어로 작성 되어 있으면

  ---<cite>incompatible character encodings: ASCII-8BIT and UTF-8</cite>

  이라는 에러가 나니까 주의하도록 하자.

  * 참고로 카테고리 이름이 한글일 경우에도, localhost:4000를 이용한다면 위와 같은 오류가 날 수 있다.

    ![](http://drive.google.com/uc?export=view&id=1HMcEVEnUI-7ESE_CSzubvEb6Ek5Jixq-)
