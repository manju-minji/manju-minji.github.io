---
title: "google drive에 있는 이미지 외부 링크 만들기"
comments: true
categories:
  - 생활
tags:
  - google drive
show_date: true
last_modified_at: 2020-08-29
---

github 블로그를 작성할 때 이미지를 넣는 방법은 다양하게 있다.



repository에 직접 이미지를 넣어도 되고(하지만 이것은 용량에 한계가...)

약간의 꼼수(?)으로 용량 측정의 대상이 아닌 issue를 이용하는 방법도 있고

자신이 이용하는 클라우드를 사용해도 된다.



본인은 구글 드라이브를 사용하고 있으므로 구글 드라이브에 이미지를 업로드하여 링크를 걸어서 이미지를 넣으려고 했다.



하지만 왠걸!

![](http://drive.google.com/uc?export=view&id=1ShJk_aZGUNSZZOaZmpbatXgyASrlR-Sh)

이런 식으로 이미지가 깨져서 나왔다...



구글링을 통해 그 이유를 알아보니

<cite>"구글 드라이브의 공유 주소로는 구글이 제공하는 뷰어에서만 볼 수 있다"고 한다.</cite>



그래서 구글 드라이브의 공유 주소를 바로 사용하면 안되고, 외부 링크로 변환해주는 과정이 필요하다고 한다.



구글 드라이브에서 원하는 파일을 우클릭하면 __공유 가능한 링크 가져오기__ 라는 항목이 있다.

이 항목을 누르면 링크가 나온다.



이때,

<img src="http://drive.google.com/uc?export=view&id=1ozMdEtzKPX7qcKppVRWMKDeTj-KBy7Jn" style="zoom:67%;" />

비공개가 아닌, __모든 사용자에게 공개__ 로 설정되어 있어야 링크를 넣었을 때 이미지가 제대로 뜬다.



[주소 변환하기](_layouts\google-drive-path.html).