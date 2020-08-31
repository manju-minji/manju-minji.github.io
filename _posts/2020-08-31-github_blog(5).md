---
title: "Github 블로그 만들기(5) - 검색 가능하게 만들기"
comments: true
classes: wide
categories:
  - github blog
tags:
  - github
  - 검색
show_date: true
last_modified_at: 2020-08-31
---

### 블로그 검색 가능하게 만들기

1. site map, RSS feed, robots.txt 생성

   * 내가 사용하는 jekyll 테마인 '[minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)'의 경우에는 이미 다 생성되어 있어서 할 필요가 없다.
   * 하지만 __sitemap.xml__ 과 __feed.xml__, __robots.txt__ 가 없는 경우에는 생성해줘야 한다.
     * [생성하는 방법 글](http://jinyongjeong.github.io/2017/01/13/blog_make_searched/) 에 들어가면 그 방법을 확인 할 수 있다.

2. 사이트 등록

   * Google

     1. [Google Search Console](https://search.google.com/search-console/about?hl=ko&utm_source=wmx&utm_medium=wmx-welcome) 에 접속한다.

     ![](http://drive.google.com/uc?export=view&id=1ye_-QLUJKWkVn_zTke1pO_iRkfrvWn-u)

     2. 구매한 도메인이 따로 없으므로 __URL 접두어__ 에서 본인의 블로그 주소(https://manju-minji.github.io/)를 통째로 넣는다.

     3. 소유권 인증

        ![](http://drive.google.com/uc?export=view&id=1FHnjV2Au9SOCBwUvga4qm50xP6tPc_nr)

        사이트의 소유권자만이 구글 검색을 허가 할 수 있기 때문에 진행하는 절차다.

        1. 제공하는 html파일을 다운 받아서, 자신의 블로그의 __root 디렉토리__ 에 넣는다.

           * 아무데나 넣으면 된다.

        2. github에 commit 한다.

        3. 확인을 누르면

           ![](http://drive.google.com/uc?export=view&id=1PV0p1TPXVkYhoP_VEUZitLI6ALDgCT9P)

           확인 되었다는 창이 나오면 정상적으로 된 것이다.

     4. sitemap.xml 제출

        ![](http://drive.google.com/uc?export=view&id=1jdmTznoOJ7lqjOQWSLZrS5AyaWK4qq-s)

        Sitemaps 메뉴에 들어가서 위의 이미지 처럼 sitemap.xml을 제출한다.
        
        제출에 성공하면 다음과 같이 된다.
        
        ![](http://drive.google.com/uc?export=view&id=1t62PCr5UlgwGvOgKm06dMXpuxyFexiRZ)
        
        {: .notice--success}
        
        __참고__ : 검색 노출까지 일주일 정도의 시간이 소모된다고 한다.
        
        
        
        