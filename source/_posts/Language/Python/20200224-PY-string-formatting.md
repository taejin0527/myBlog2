---
title: (PYTHON) 문자열 포맷팅
date: 2020-02-24 22:39:14
categories:
  - LANGUAGE 🚀
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

# String Formatting

- Python 3.8 공식 문서를 보면 3가지 방법이 소개 되어 있습니다.(manual formatting 생략)

## Formatted String Literals

줄여서 **f-strings** 라고 불립니다. <mark>파이썬 3.6 버전 이상</mark>부터 지원합니다.
문자열 `''` 앞에 `f` 혹은 `F` 를 붙여서 사용하며 변수는 `{}` 안에 변수명으로 호출합니다.(`{}` 안의 공간을 format field라고 부릅니다.)
{% code lang:python %}

> > > import math
> > > print(f'The value of pi is approximately {math.pi}.')
> > > The value of pi is approximately 3.141592653589793. {% endcode %}

`{expression}` 안에 `:` 뒤에 optional format specifier를 지정할 수 있습니다.
{% code lang:python %}

> > > # optional format specifier 지정
> > >
> > > print(F'The value of pi is approximately {math.pi:.3f}.')
> > > The value of pi is approximately 3.142.

> > > # 문자열의 공간을 지정할 수 도 있습니다
> > >
> > > table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 7678}
> > > for name, phone in table.items():
> > > ... print(f'{name:10} ==> {phone:10d}')
> > > ...
> > > Sjoerd ==> 4127
> > > Jack ==> 4098
> > > Dcab ==> 7678{% endcode %}

`{}` 안에서 기본적인 산술 연산이 가능합니다.
{% code lang:python %}

> > > a, b = 5, 7
> > > print(f'{a + b}')
> > > 12 {% endcode %}

호출할 변수를 나중에 선언하는 것도 가능합니다.
{% code lang:python %}

> > > h = f'Hello {w}'
> > > w = 'World!'
> > > print(h)
> > > Hello World! {% endcode %}

## str.format() Method

문자열 `''` 뒤에 `.format()` 함수를 붙여 사용하는 방법입니다.
{% code lang:python %}

> > > print('We are the {} who say "{}!"'.format('knights', 'Ni'))
> > > We are the knights who say "Ni!" {% endcode %}

`format()` 함수 안에 있는 객체들이 format field 즉, `{}` 안의 내용으로 대입됩니다. Format field 안에 번호를 붙여줌으로 객체들의 순서를 바꿀 수도 있습니다.
{% code lang:python %}

> > > print('{0} and {1}'.format('spam', 'eggs'))
> > > spam and eggs
> > > print('{1} and {0}'.format('spam', 'eggs'))
> > > eggs and spam {% endcode %}

Format field에는 숫자뿐만이 아니라 keyword 이름으로 넣을 수 있습니다.
{% code lang:python %}

> > > print('The story of {0}, {1}, and {other}.'.format('Bill', 'Manfred', other='Georg'))
> > > The story of Bill, Manfred, and Georg. {% endcode %}

## Old string formatting

C 언어의 `printf` 방식과 비슷한 방법입니다.
**데이터 타입에 맞춰서 `%` 뒤에 오는 문자를 지정해 줘야하고 가독성이 떨어지는** 단점이 있습니다.
(int 타입이지만 `%s` 를 사용해도 왜 정상적으로 출력되는 이유를 잘 모르겠습니다ㅠ 반대로하면 {% label danger@TypeError: %d format: a number is required, not type %} 에러가 출력됩니다.)

{% code lang:python %}

# example 1

> > > text = 'World!'
> > > print('Hello %s' % text)  
> > >  Hello World!

# example 2

> > > name = 'Eric Idle'
> > > age = 74
> > > job = 'comedian'
> > > affiliation = 'Monty Python'

> > > print('Hello %s. You are %d. You are a %s. You were a member of %s' % (name, age, job, affiliation))
> > > Hello Eric Idle. You are 74. You are a comedian. You were a member of Monty Python
> > > print('You are %s. Type? %s' % (age, type(age)))  
> > >  You are 74. Type? <class 'int'> {% endcode %}

# 비교

{% code lang:python %}

# time.py written in PyCharm

from timeit import timeit

print('f-string: ', timeit("f'{name} is {age}'", setup='name = "Guido"; age=64'))
print('format(): ', timeit("'{} is {}'.format(name, age)", setup='name = "Guido"; age=64'))
print('% operator:', timeit("'%s is %s' % (name, age)", setup='name = "Guido"; age=64')) {% endcode %}

{% code lang:python %}
f-string: 0.22740733000000002
format(): 0.471766373
% operator: 0.3950569239999999 {% endcode %}

**f-string** 방식이 가장 빠른 것을 확인할 수 있습니다.

# 결론

{% note info %}
Formatted String Literals 즉, f-string 사용을 권장합니다.
{% endnote %}

---

---
