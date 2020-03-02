---
title: (PYTHON) 파이썬의 easter egg
date: 2020-02-25 16:28:32
categories:
  - LANGUAGE
  - PYTHON
  - TERMINOLOGY
tags: [파이썬, programming language, python, language]
subtitle: 용어 정리
---

# Reference

- antigravity.py 소스코드 - [github.com/python/cpython/...](https://github.com/python/cpython/blob/master/Lib/antigravity.py#L7-L17)
- xkcd 링크 - [xkcd.com/353](https://xkcd.com/353/)
- python easter eggs - [repl.it/talk](https://repl.it/talk/share/Python-Easter-Egg/25634)
- Curated list of all the easter eggs and hidden jokes in Python - [github.com/OrkoHunter/](https://github.com/OrkoHunter/python-easter-eggs)
- 파이썬 선 번역 - [kenial.tistory.com](https://kenial.tistory.com/903)
- sytax error not a chance - [stackoverflow.com](https://stackoverflow.com/questions/17811855/syntax-error-not-a-chance)

---

{% note info %}
이메일로 받아보는 [🐍PyTricks]를 통해서 CPython에 있는 이스터에그(easter egg) 하나를 알게되었습니다.
{% endnote %}


# Antigravity

우선 [🐍PyTricks]를 통해 알게된 Antigravity 모듈을 먼저 알아보겠습니다.

{% code lang:python %}
import antigravity {% endcode %}

antigravity 모듈을 호출하게되면 xkcd 홈페이지가 열리면서 짧은 만화를 볼 수 있습니다.

{% gp 2-2 %}
<img src='https://imgs.xkcd.com/comics/python.png'>
<img src='https://ww.namu.la/s/adb574b12427b293e0f08880f5c40746498afc9c3873d14a9bb9ee2bac99bfbd5a15f8aa6244ea78e60b378bb642b6cf5782ba40a7bd451368e5fe1171b0ae689515651c34fccaa0e505dd6673298c9432104cef2299ae62c57ddcde31793582'>
{% endgp %}

<div style="text-align:center">(Left: 원본, Right: 한국어 번역)</div>

파이썬의 철학을 간결하고 재치있게 4컷 만화에 담았습니다.
여기서 끝이 아니라 `antigravity.py` 소스코드를 살펴보게 되면,

{% code lang:python %}
import webbrowser
import hashlib

webbrowser.open("https://xkcd.com/353/")

def geohash(latitude, longitude, datedow):
    '''Compute geohash() using the Munroe algorithm.
    >>> geohash(37.421542, -122.085589, b'2005-05-26-10458.68')
    37.857713 -122.544543
    '''
    # https://xkcd.com/426/
    h = hashlib.md5(datedow).hexdigest()
    p, q = [('%f' % float.fromhex('0.' + x)) for x in (h[:16], h[16:32])]
    print('%d%s %d%s' % (latitude, p[1:], longitude, q[1:])) {% endcode %}

`geohash()` 함수가 숨어있는 것을 확인할 수 있으며 이에 대한 설명은 xkcd 홈페이지에서 찾을 수 있습니다.

<img src='https://imgs.xkcd.com/comics/geohashing.png'>

---

{% note info %}
이참에 Python의 다른 이스터에그는 어떤 것들이 있는지 찾아보았습니다.
{% endnote %}


# Hello World!

프로그래밍을 배우는 사람이라면 꼭 외치는 한마디가 있죠.

{% code lang:python %}
>>> import __hello__
Hello World! {% endcode %}

# The Zen of Python

`this` 모듈을 호출하면 파이썬의 철학 (the zen of python)의 전문을 바로 확인할 수 있습니다.

{% code lang:python %}
>>> import this

The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than right now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those! {% endcode %}

한글 번역은 다음과 같습니다. (임의로 앞에 번호를 붙였습니다)
{% code %}
1 아름다움이 추함보다 좋다.
2 명시가 암시보다 좋다.
3 단순함이 복잡함보다 좋다.
4 복잡함이 꼬인 것보다 좋다.
5 수평이 계층보다 좋다.
6 여유로운 것이 밀집한 것보다 좋다.
7 가독성은 중요하다.
8 특별한 경우라는 것은 규칙을 어겨야 할 정도로 특별한 것이 아니다.
9 허나 실용성은 순수성에 우선한다.
10 오류 앞에서 절대 침묵하지 말지어다.
11 명시적으로 오류를 감추려는 의도가 아니라면.
12 모호함을 앞에 두고, 이를 유추하겠다는 유혹을 버려라.
13 어떤 일에든 명확한 - 바람직하며 유일한 - 방법이 존재한다.
14 비록 그대가 우둔하여 그 방법이 처음에는 명확해 보이지 않을지라도.
15 지금 하는게 아예 안하는 것보다 낫다.
16 아예 안하는 것이 지금 당장 보다 나을 때도 있지만.
17 구현 결과를 설명하기 어렵다면, 그 아이디어는 나쁘다.
18 구현 결과를 설명하기 쉽다면, 그 아이디어는 좋은 아이디어일 수 있다.
19 네임스페이스는 대박 좋은 아이디어다 -- 마구 남용해라! {% endcode %}

{% label primary@ 파이썬 핵심 개발자 Tim Peters가 제안한 가이드라인은 20개이며 빠진 내용은 “some bizarre Tim Peters in-joke.” 입니다. 누가 파이썬 창시자인 귀도 반 로섬에게 질문하고 들은 내용이라고 합니다%}
삭제된 하나의 가이드라인은 무엇이죠? - [stackoverflow](https://stackoverflow.com/questions/4504487/the-zen-of-python-distils-the-guiding-principles-for-python-into-20-aphorisms-bu/4504891)

# C-style braces

아시다싶이 Python에서는 코드 블록을 구분할 때 괄호(brace)를 사용하지 않고 들여쓰기(indentation)를 사용합니다.
프로그래머 마다 각자 선호하는 코딩 스타일이 있고 이는 마치 종교처럼 나뉘어져 있습니다.
종교의 자유가 있듯이 파이썬에서도 괄호를 사용하는 코드 스타일을 허용해 줄까요?

{% code lang:python %}
>>> from __future__ import braces
  File "<stdin>", line 1
  SyntaxError: not a chance {% endcode %}

~~ **어림도 없지!!!** ~~
`__future__` 모듈은 파이썬 2, 3 사이의 호환성 문제를 해결하기 위한 모듈입니다. 파이썬 2에서도 파이썬 3에서 사용하는 문법을 쓸수 있도록 해줍니다. 단어대로 해석하자면 미래에 사용되는 ~한 기능을 가져와서 사용하겠다가 되겠습니다.
괄호 사용을 선호하는 프로그래머를 위해 braces 기능을 넣어주겠지? 하는 마음에 모듈을 호출해보면 SyntaxError로 {% label danger@not a chance %} 라고 그럴일은 없다고 단호하게 출력되는 것이 _유머_ 입니다.

{% code lang:python %}
>>> from __future__ import test
  File "<stdin>", line 1
  SyntaxError: future feature test is not defined {% endcode %}

`__future__` 모듈에 없는 임의의 모듈을 호출하면 그냥 선언되어 있지 않다고 왠지 모르게 밋밋한 답변을 볼 수 있습니다.

---
---
