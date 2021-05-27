---
title: (PYTHON) pow() vs math.pow()
date: 2020-03-02 22:37:17
categories:
  - LANGUAGE 🚀
  - PYTHON
  - TERMINOLOGY
tags: [파이썬, programming language, python, language]
subtitle: 용어 정리
---

# Reference

- Difference between pow() and math.pow()- [stackoverflow.com](https://stackoverflow.com/questions/10282674/difference-between-the-built-in-pow-and-math-pow-for-floats-in-python)
- Python pow - [journaldev.com](https://www.journaldev.com/23002/python-pow)
- 파이썬에서 제곱을 할때요 - [edu.groom.io](https://edu.goorm.io/qna/2013)
- Built-in pow() - [Python Documentation](https://docs.python.org/3/library/functions.html#pow)
- Math pow() - [Python Documentation](https://docs.python.org/3/library/math.html#math.pow)

> 개인적인 생각과 상상으로 작성한 내용들이 포함되어 있습니다

---

{% note info %}
{% label primary @ math 모듈 %}을 살펴보다가 기본 내장함수 `pow()`가 있는데 왜 굳이 `math.pow()`를 정의해 뒀을까 궁금해서 검색한 내용들을 정리해봤습니다.

<img style='display:block; margin-left: auto; margin-right: auto;' src='https://imgs.xkcd.com/comics/powers_of_one.png'>

> 짧은 다큐멘터리 [Youtube링크 - Powers of Ten™ (1977)](https://youtu.be/0fKBhvDjuy0)를 패러디한 만화입니다

{% endnote %}

# 단순한 비교

{% note no-icon %}
두 함수의 정의를 봤을 때, 내장함수 `pow()`에만 augment 하나가 더 옵션으로 들어갈 수 있는 것을 볼 수 있습니다.
{% note primary no-icon %}
pow(base, exp[, mod])
math.pow(x, y)
{% endnote %}

코드를 작성해서 확인해봐도 둘은 분명히 다른 함수인 것을 알 수 있습니다.
{% code lang:python %}

> > > import math
> > > print(pow is math.pow)
> > > False {% endcode %}

{% endnote %}

</br>

# Built-in pow()

{% note no-icon %}
`pow(base, exp)` 이렇게 2개의 인자(augment)만 주어진다면 밑(base)의 지수(exp)승(또는, base의 exp제곱)한 값을 반환합니다. 반환되는 값의 자료형은 인자들의 자료형을 따라 Integer, Float, Complex number 등으로 결정됩니다.
<mark>`base ** exp`는 `pow(base, exp)`와 똑같은 기능을 합니다.</mark>

{% code lang:python %} >>> print(pow(10, 2))
100

    >>> print(pow(10.0, 2))
    100.0

    >>> print(pow(2 + 3j, 2))
    -5+12j

    >>> print(pow(0b11, 2))  # 0b11 = 3
    9

    >>> print(pow(100.0, 2, 3))
    TypeError: pow() 3rd argument not allowed unless all arguments are integers
    >>> print(pow(100, -1, 2))
    ValueError: pow() 2nd argument cannot be negative when 3rd argument specified {% endcode %}

`pow(base, exp, mod)` 세번째 인자[, mod]를 입력하면 base의 exp제곱한 값에 mod를 나눈 나머지 값을 반환합니다. 특히 세번째 인자가 있을 때, base와 exp는 정수형이여야 하고 exp는 양수 값이여야 합니다. <mark>`pow(base, exp, mod)`를 사용하는 것이 `pow(base, exp) % mod`로 계산하는 것 보다 효율적입니다.</mark>

{% code lang:python %} >>> print(pow(10, 2, 3)) # 10^2 % 3
1 >>> print(pow(10, 2) % 3)
1

    >>> print(pow(0b11, 2, 2))   # 9^2 % 2
    1 {% endcode %}

{% endnote %}

# math.pow()

{% note no-icon %}
`math.pow(x, y)` 함수는 순수하게 거듭제곱의 연산 기능만 제공합니다.
`pow(base, exp)` 함수 혹은 `**` 연산자와 다른 점으로 `math.pow(x,y)` 함수는 {% label danger@ 두 인자를 float 형으로 바꾼다는 점 %}입니다.

- `pow(1.0, x)`이나 `pow(x, 0.0)`의 결과값은 무조건 1.0을 반환합니다.(x가 0이거나 NaN 값이라도)

{% code lang:python %}
import math

    inf = float("inf")
    NaN = float("nan")
    p = [inf, -inf, NaN, 0.0, -0.0, 0]

    for x in p:
        print("x is", f'{x:4} /', "pow(1.0, x)=", math.pow(1.0, x), "pow(x, 0.0)=", math.pow(x, 0.0)) {% endcode %}

{% code lang:python %}
x is inf / pow(1.0, x)= 1.0 pow(x, 0.0)= 1.0
x is -inf / pow(1.0, x)= 1.0 pow(x, 0.0)= 1.0
x is nan / pow(1.0, x)= 1.0 pow(x, 0.0)= 1.0
x is 0.0 / pow(1.0, x)= 1.0 pow(x, 0.0)= 1.0
x is -0.0 / pow(1.0, x)= 1.0 pow(x, 0.0)= 1.0
x is 0 / pow(1.0, x)= 1.0 pow(x, 0.0)= 1.0 {% endcode %}

- `pow(x, y)`에서 x와 y가 finite하고, x가 음수이고, y가 정수가 아니면 {% label danger@ ValueError %}를 반환합니다.

{% code lang:python %}
vals = [(1.23, 3.33), (-1.23, 2.0), (-1.23, -3.33)]
for x, y in vals:
print(f"x is {x}, y is {y} /", math.pow(x, y)) {% endcode %}

{% code lang:python %}
x is 1.23, y is 3.33 / 1.9924343529238528
x is -1.23, y is 2.0 / 1.5129
ValueError: math domain error {% endcode %}
{% endnote %}

# 수행시간 비교

{% note no-icon %}

{% code lang:python %} # executionTime.py written in PyCharm
from timeit import timeit

    print('Int ** Int'.ljust(30), timeit('7 ** 5'))
    print('pow(Int, Int)'.ljust(30), timeit('pow(7, 5)'))
    print('math.pow(Int, Int)'.ljust(30), timeit('math.pow(7, 5)', setup='import math'))
    print()
    print('float ** float'.ljust(30), timeit('7.0 ** 5.0'))
    print('pow(float, float)'.ljust(30), timeit('pow(7.0, 5.0)'))
    print('math.pow(float, float)'.ljust(30), timeit('math.pow(7.0, 5.0)', setup='import math')) {% endcode %}

{% label primary@ `**` 연산자가 큰 차이로 가장 빠르고 `pow()`와 `math.pow()`는 비슷비슷한 시간을 가집니다. %}

{% code lang:python %}
Int \*\* Int 0.012045001
pow(Int, Int) 0.497163934
math.pow(Int, Int) 0.24036590000000002

    float ** float                 0.012131208999999976
    pow(float, float)              0.156296341
    math.pow(float, float)         0.21024002100000005 {% endcode %}

{% endnote %}

# 결론

{% note info no-icon %}
입력되는 인자의 자료형과 상관없이 반환값을 무조건 실수형(float)으로 받고 싶을 때 `math.pow()` 함수를 사용하는 것이 좋습니다.
{% code lang:python %}

> > > timeit('float(i) ** j', setup='i, j = 7, 5')
> > > 0.7610865891750791
> > > timeit('i ** float(j)', setup='i, j = 7, 5')
> > > 0.7930400942188385
> > > timeit('float(i \*\* j)', setup='i, j = 7, 5')
> > > 0.8946636625872202
> > > timeit('math.pow(i, j)', setup='import math; i, j = 7, 5')
> > > 0.5699394063529439 {% endcode %}

위 코드 결과와 같이, 정수형으로 반환되는 `**` 연산(혹은 `pow()`) 결과를 `float()` 함수로 형변환 하는 것 보다 `math.pow()` 함수가 더 빠른 것을 볼 수 있습니다.

{% label danger@ 특별한 경우가 아니고 간단한 연산에 필요하다면 `**` 연산자를 사용하는 것이 가장 좋을 듯 합니다 %}

{% endnote %}

---

---
