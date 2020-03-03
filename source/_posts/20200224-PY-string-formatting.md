---
title: (PYTHON) 문자열 포맷팅
date: 2020-02-24 22:39:14
categories:
  - LANGUAGE
  - PYTHON
  - TERMINOLOGY
tags: [파이썬, programming language, python, language]
subtitle: 용어 정리
---

# Reference

- Python 공식 문서 - [7. Input and Output](https://docs.python.org/3/tutorial/inputoutput.html)

> 개인적인 생각과 상상으로 작성한 내용들이 포함되어 있습니다

---

{% note info %}
(본 내용에서 파일 입/출력은 생략하겠습니다)
조금 과장되게 말해서 파이썬에서 입력과 출력은 `input()` 함수와 `print()` 함수만 알면 끝입니다.
파이썬은 `input()` 함수를 통해 입력되는 모든 것을 string 자료형으로 통일시켜 마치 쌈 싸서 한 입에 먹는 것 처럼 처리합니다. (이 한 뭉텅이의 입력 데이터를 연산의 필요에 따라 `int`, `list` 등의 다른 자료형으로 변환시키거나 특정 구분자로 `split()` 함수를 사용해 분리시키기도 합니다. 중요한건 들어올 때는 참 쉽다는 것입니다.)
어떻게 입력 받는지 보다 어떻게 출력 되는지가 더 중요하다는 것은 아닙니다. 하지만 '보기 좋은 떡이 먹기도 좋다' 라는 속담이 있듯이 많은 사람들이 입력 보단 프로그램의 결과물인 출력 방법에 더 정성을 쏟는 것 같습니다.
{% endnote %}

<img src="https://www.izscomic.com/wp-content/uploads/2016/06/Hard-to-escape.jpg">

~마치 파이썬과 나의 관계...~

# String Formatting

- Python 3.8 공식 문서를 보면 4가지 방법이 소개 되어 있습니다.

## Formatted String Literals

줄여서 **f-strings** 라고 불립니다.
문자열 `''` 앞에 `f` 혹은 `F` 를 붙여서 사용합니다.
`{expression}` 안의 `:`
{% code lang:python %}
>>> import math
>>> print(f'The value of pi is approximately {math.pi}.')
The value of pi is approximately 3.141592653589793.

>>> print(F'The value of pi is approximately {math.pi:.3f}.')
The value of pi is approximately 3.142. {% endcode %}

## str.format() Method


## Manual string Formatting



## Old string formatting

{% code lang:python %}
  # example 1
  >>> text = 'World!'
  >>> print('Hello %s' % text)  
  Hello World!

  # example 2
  >>> name = 'Eric Idle'
  >>> age = 74
  >>> job = 'comedian'
  >>> affiliation = 'Monty Python'

  >>> print('Hello %s. You are %d. You are a %s. You were a member of %s' % (name, age, job, affiliation))
  Hello Eric Idle. You are 74. You are a comedian. You were a member of Monty Python
  >>> print('You are %s. Type? %s' % (age, type(age)))  
  You are 74. Type? <class 'int'> {% endcode %}

C 언어의 `printf` 방식과 비슷한 방법입니다.
**데이터 타입에 맞춰서 `%` 뒤에 오는 문자를 지정해 줘야하고 가독성이 떨어지는** 단점이 있습니다.
(int 타입이지만 `%s` 를 사용해도 왜 정상적으로 출력되는 이유를 잘 모르겠습니다ㅠ 반대로하면 {% label danger@TypeError: %d format: a number is required, not type %} 에러가 출력됩니다.)

---
---
