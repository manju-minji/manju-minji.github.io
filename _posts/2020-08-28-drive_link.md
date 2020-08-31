---
title: "google drive에 있는 이미지 외부 링크 만들기"
comments: true
classes: wide
categories:
  - life
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



## 주소 변환하기

<html>
<head>
  <!-- Latest compiled and minified CSS -->
 
  <style>
    #converter {
      padding: 20px 20px;
      border-radius: 5px;
      background-color: #c7efdf;
      width: 100%;
      padding: 15px 15px;
    }

    #converter textarea {
      display: block;
      white-space: wrap;
      border: 1px solid #888;
      border-radius: 5px;
      margin-bottom: 10px;
      padding: 5px 5px;
      width: 100%;
      height: 60px;
    }
    
    #converter label {
      font-weight: bold;
      color: #333;
    }
    
    #converter button {
      font-weight: bold;
    }
    
    #btn-convert {
      width: 100%;
    }
    
    #convert-result {
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <div id="converter">
    <label>Google Drive path</label>
    <textarea id="gd-url" placeholder="Input Google Drive Url"></textarea>
    <button id="btn-convert" class="btn btn-primary">Make Google Drive Path Linkable</button>
    <div id="convert-result">
      <label for="result">Linkable Image path</label>
      <textarea id="result" name="result" readonly></textarea>
      <button id="btn-save-result-cb" class="btn btn-success pull-right" data-clipboard-target="#result">
        <span class="glyphicon glyphicon-copy" aria-hidden="true"></span>
        Save to Clipboard
      </button>
      <br><br>
      <label for="result-img-tag">Image Tag</label>
      <textarea id="result-img-tag" name="result" readonly></textarea>
      <button id="btn-save-result-img-tag-cb" class="btn btn-success pull-right" data-clipboard-target="#result-img-tag">
        <span class="glyphicon glyphicon-copy" aria-hidden="true"></span>
        Save to Clipboard
      </button>
    </div>
    <br><br><br>
      <p align="center">
      <b>Preview image</b>
      </p>
    <p align="center">
      <img id="preview" alt="image preview" src='https://www.google.com/drive/static/images/drive/logo-drive.png' class="img-thumbnail" style="max-width: 200px"/><br>
    </p>

  </div>

  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/clipboard.js/1.7.1/clipboard.min.js"></script>
  <script>
    var gdUrl = $("#gd-url");
    $("#btn-convert").on("click", function(event) {

      if (!isValidUrl(gdUrl.val())) {
        alert("You have inputted invalid path.");
        gdUrl.val("");
        return;
      }
    
      var gdId = extractFileId(gdUrl.val());
      var prefix = "http://drive.google.com/uc?export=view&id=";
      $("#result").val(prefix + gdId);
      $("#result-img-tag").val(
        "<img src='" +
        prefix + gdId +
        "' /><br>");
      $("#preview").attr("src", prefix + gdId);
    });
    
    var clipboard = new Clipboard('.btn');
    
    clipboard.on('success', function(e) {
      console.info('Action:', e.action);
      console.info('Text:', e.text);
      console.info('Trigger:', e.trigger);
    
      e.clearSelection();
    });
    
    clipboard.on('error', function(e) {
      console.error('Action:', e.action);
      console.error('Trigger:', e.trigger);
    });
    
    // validity check. ref: https://gist.github.com/jlong/2428561
    function isValidUrl(url) {
      // to be impl...
      var parser = document.createElement('a');
      parser.href = url;
    
      if(url === '' || parser.hostname !== "drive.google.com" || !parser.pathname.includes("/file/d/"))
        return false;
    
      return true;
    }
    
    function extractFileId(url) {
      if (!url)
        url = window.location.href;
    
      var strip = url.replace(/https:\/\/drive.google.com\/file\/d\//gi, "")
      .replace(/\/view\?[a-zA-Z=\/]+/gi, "");
    
      return strip;
    }
  </script>
</body>

</html>

[참고 링크](http://www.somanet.xyz/2017/06/blog-post_21.html)

여기서 주소 변환 방법은

https://drive.google.com/file/d/'파일의 id 부분'/view?usp=sharing

원래 링크의 파일의 id 부분을 가져와서

http://drive.google.com/uc?export=view&id='파일의 id 부분'

이렇게 넣어주는 것이다.