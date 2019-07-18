---
title: (Hexo_NexT_Theme) Hexo 블로그에 Google Adsense 설정
date: 2019-07-17 14:09:11
categories:
  - BLOG
  - HEXO-NEXT-THEME
tags: [헥소, 블로그, 테마, adsense, hexo, blog, next-theme, github page]
subtitle: Hexo-next-theme 설정
---

{% note info %}
Hexo-NexT-Theme 에 구글 애드센스를 추가하는 방법에 대해 알아보겠습니다!
{% endnote %}

{% fi /img/adsense_home.png %}

홈페이지에 접속하여 구글 계정으로 로그인하고 구글 애드센스에 가입하는 방법은 인터넷에 검색하면 금방 찾으실 수 있습니다.

간략하게 설명드리자면 구글 검색엔진에 등록하는 것과 비슷한 방식으로 <u>광고를 등록하고자 하는 웹사이트 URL를 입력</u>하고 <u>이메일 주소를 입력</u>하면 됩니다.

중요한 것은 **애드센스 활성화** 를 하기 위해서는 HTML 문서를 수정해야 하는데 하나하나 모든 포스트의 HTML 문서를 수정하는 것은 시간 낭비 같습니다.
(만약 `hexo clean`으로 초기화 하고 다시 `hexo generate` 하게되면 헛고생 한게 되니...)
`hexo generate`를 통해 markdown 문서와 여러 javascript 파일들을 통해 포스트를 생성하기 때문에 **javascript** 를 손보면 해결될 것 같은 느낌이듭니다.

## `google_adsense.ejs` 파일 생성

```
/themes/hexo-theme-next/layout/_custom/google_adsense.ejs
```

{% fi /img/theme_layout.png %}

테마가 설치된 경로의 `layout`폴더에 `_custom` 폴더가 없다면 생성하시고 있으시면 그 안에 `google_adsense.ejs` 파일을 새로 생성합니다.

## Adsense 코드 복사

생성된  `google_adsense.ejs` 파일에 사이트 검토를 위한 소스 코드를 복사 붙여 넣기합니다. (아래는 예시로 google_ad_client의 키 값이 없습니다)

{% code lang:javascript %}
<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<script>
  (adsbygoogle = window.adsbygoogle || []).push({
    google_ad_client: "your key",
    enable_page_level_ads: true
  });
</script>
{% endcode %}

## `_layout.swig` 파일의 <head> 수정

`_layout.swig` 파일이 블로그 포스트의 전체적인 레이아웃을 담당하고 있는 것을 알 수 있습니다.
여기 <head></head> 태그 안에 저희가 생성한 javascript 파일을 넣으면 됩니다.

```html
  <!-- Google AdSense start -->
  {% include '_custom/google_adsense.ejs' %}
  <!-- Google AdSense end -->
```

## `hexo generate` 후 확인하기

`hexo g -d` 한 후 블로그의 소스코드 보기를 통해 저희가 작성한 코드가 잘 적용되어 있는지 확인할 수 있습니다.
구글 애드센스 사이트 검증을 요청하면 아래와 같은 화면을 보실 수 있습니다.

{% fi /img/adsense_wait.png %}
