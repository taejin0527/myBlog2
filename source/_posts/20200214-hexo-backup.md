---
title: (Hexo_NexT_Theme) 블로그 백업
date: 2020-02-14 17:59:51
categories:
- BLOG
- HEXO-NEXT-THEME
tags: [헥소, 블로그, 테마, hexo, blog, next-theme, github page]
subtitle: 블로그 포스팅 하는데 도움되는 정보들
---

{% note info %}
Github에 모든 파일을 다 올렸다고 생각했는데,
막상 `git clone` 을 해보니 테마 파일이 빠져있음을 알게 되었다.
{% endnote %}

---

# 사라진 hexo-theme-NexT

연습삼아 모든 파일을 지우고 깃허브에 업로드한 데이터를 다운받고 실행시키는데 문제가 발생했다.

hexo 자체의 문제는 없고 특정 태그를 인식 못하는 것을 보고 테마 설정에 문제 있는 것을 인지하였다.

`git clone` 을 통해 다운받은 폴더를 살펴보니 `hexo-theme-NexT` 폴더 안 내용이 비어있음을 발견했다.

분명 `.gitignore` 파일에는 아무것도 작성하지 않고 모든 파일 및 디렉토리가 깃에 업로드 되도록 설정한 것 같은데,
`themes` 폴더 안의 `hexo-theme-NexT` 내용이 제대로 업로드 되지 않음을 이번에 알게 되었다.

{% fi /img/200214_github.png %}


# 임기응변으로 해결

그래서 다시 `git clone https://github.com/theme-next/hexo-theme-next.git` 을 통해 테마를 다운 받아 넣었는데,
원본에서 조금 커스터마이즈했던 설정들 때문에 정상적으로 작동이 되지 않았다.

`_config.yml` 파일의 내용을 하나하나 수정할 수 밖에 없는 것 같아서
혹시나 하고 백업 파일로 남겨둔 기존 데이터를 그냥 덮어씌우는 방식으로 문제를 해결했다.

# 테마 전용 저장소 생성

블로그의 테마들은 각자의 git을 가지고 있기 때문에 전체 데이터를 관리하는 git 아래 테마 폴더만의 git이 존재하는 꼴이 된다

이처럼 git 안에 git이 있는 경우 submodule 로 관리하는 것이 좋다고 한다
