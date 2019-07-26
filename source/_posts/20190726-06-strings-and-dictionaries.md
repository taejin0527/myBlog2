---
title: (파이썬) 06 Strings and Dictionaries
date: 2019-07-26 22:11:36
categories:
  - LANGUAGE
  - PYTHON
tags: [파이썬, 캐글, 튜토리얼, kaggle, programming language, python, language, strings, dictionaries, tutorial]
subtitle: Kaggle 홈페이지 Python 강좌 참고
---

# Reference

- Kaggle 홈페이지 - [Kaggle](https://www.kaggle.com)
- 11강 'Strings and Dictionaries' - [Python Micro-Course Home Page](https://www.kaggle.com/colinmorris/strings-and-dictionaries)

> 영어 실력이 부족하여 문맥이 이해가 가지 않는 부분은 원문을 참고하시길 바랍니다...
> 언젠가는 실력이 나아지기를...

------

이번 강에서는 파이썬의 필수적인 타입인 **strings** 와 **dictionaries** 에 대해 알아보겠습니다.

# 문자열(Strings)

파이썬의 장점이 빛나는 순간 중 하나는 문자열을 조작할 때 입니다. 이번 섹션에서 파이썬에 내장된 문자열 함수들과 포맷팅 작업들에 대해 알아보겠습니다.

문자열 조작 패턴들은 데이터 사이언스(데이터 분석/마이닝) 작업할 때 자주 등장하는데, 이런 맥락에서 볼 때 문자열 조작은 파이썬의 큰 장점 중 하나라고 할 수 있습니다.

## 문자열 문법(String syntax)

이전 수업들의 예제에서 많은 문자열들을 다루며 이미 아시겠지만, 간단히 요약하자면 파이썬의 문자열은 작은 따옴표나 큰 따옴표 중 하나를 사용하여 정의 할 수 있습니다. 둘은 기능적으로 동일합니다.

{% note no-icon %}
{% code lang:python %}
x = 'Pluto is a planet'
y = "Pluto is a planet"
x == y  {% endcode %}
{% code lang:python %}
True  {% endcode %}
{% endnote %}

문자열에 작은 따옴표가 들어가는 경우(e.g. apostrophe) 큰 따옴표를 사용하면 편리합니다.
마찬가지로 큰 따옴표가 포함된 문자열은 작은 따옴표로 묶으면 쉽게 만들 수 있습니다.

{% note no-icon %}
{% code lang:python %}
print("Pluto's a planet!")
print('My dog is named "Pluto"') {% endcode %}
{% code lang:python %}
Pluto's a planet!
My dog is named "Pluto" {% endcode %}
{% endnote %}

만약 작은 따옴표로 묶은 문자열에 작은 따옴표 문자를 넣으면 우리가 원하는 것과는 다르게 파이썬은 잘못 이해할 수 있습니다.

{% note warning no-icon %}
{% code lang:python %}
'Pluto's a planet!' {% endcode %}
{% code lang:python %}
File "<ipython-input-3-a43631749f52>", line 1
  'Pluto's a planet!'
         ^
SyntaxError: invalid syntax{% endcode %}
{% endnote %}

작은 따옴표 문자에 백슬래시로 "예외" 처리하여 이를 해결할 수는 있습니다.

{% note no-icon %}
{% code lang:python %}
'Pluto\'s a planet!' {% endcode %}
{% code lang:python %}
'Pluto's a planet!' {% endcode %}
{% endnote %}

아래의 표는 백슬래시 문자 사용법의 요약입니다.

| What you type... | What you get | example                   | `print(example)`       |
| :--------------- | :----------- | :------------------------ | :--------------------- |
| `\'`             | `'`          | `'What\'s up?'`           | `What's up?`           |
| `\"`             | `"`          | `"That's \"cool\""`       | `That's "cool"`        |
| `\\`             | `\`          | `"Look, a mountain: /\\"` | `Look, a mountain: /\` |
| `\n`             |              | `"1\n2 3"`                | `1` `2 3`              |

표 마지막의 `\n` 은 개행 문자를 나타냅니다. 이를 통해 파이썬에서 줄 바꿈이 발생합니다.

{% note no-icon %}
{% code lang:python %}
hello = "hello\nworld"
print(hello) {% endcode %}
{% code lang:python %}
hello
world {% endcode %}
{% endnote %}

또 다른 방법으로, 파이썬에서 문자열에 따옴표 세 개(triple quote syntax for strings)를 사용하면 입력하는 문자 그대로 개행 문자도 포함 할 수 있습니다.(즉, '\n' 시퀀스를 사용하지 않고 키보드에서 'Enter'키를 치는 것만으로 줄 바꿈이 일어납니다). 우리는 함수를 문서화하는 데 사용하는 docstrings 을 배우면서 이것을 한번 본적이 있는데 사실 문자열을 정의하고자 하는 곳이면 어디에서나 사용할 수 있습니다.

{% note no-icon %}
{% code lang:python %}
triplequoted_hello = """hello
world"""
print(triplequoted_hello)
triplequoted_hello == hello {% endcode %}
{% code %}
hello
world

True {% endcode %}
{% endnote %}

`print()` 함수는 `end` 키워드 인자에 특별한 값을 지정하지 않는한 기본값으로 `'\n'` 을 가지기 때문에 자동으로 개행 문자를 추가합니다.

{% note no-icon %}
{% code lang:python %}
print("hello")
print("world")
print("hello", end='')
print("pluto", end='') {% endcode %}
{% code %}
hello
world
hellopluto {% endcode %}
{% endnote %}

## Strings are sequences

## String methods

### Going between strings and lists: .split() and .join()

### Building strings with .format()


-----

# 딕셔너리(Dictionaries)

-----

<br><br><br>
# 연습문제(Your Turn)

[strings and dictionaries 예제](https://www.kaggle.com/kernels/fork/1275185)
