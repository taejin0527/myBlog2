---
title: (파이썬) 05 Loops and List Comprehensions
date: 2019-07-25 14:49:18
categories:
  - LANGUAGE 🚀
  - PYTHON
  - KAGGLE
tags: [파이썬, 캐글, 튜토리얼, kaggle, programming language, python, language, loops, list comprehensions, tutorial]
subtitle: Kaggle 홈페이지 Python 강좌 참고
---

# Reference

- Kaggle 홈페이지 - [Kaggle](https://www.kaggle.com)
- 9강 'Loops and List Comprehensions' - [Python Micro-Course Home Page](https://www.kaggle.com/colinmorris/loops-and-list-comprehensions)

> 영어 실력이 부족하여 문맥이 이해가 가지 않는 부분은 원문을 참고하시길 바랍니다...
> 언젠가는 실력이 나아지기를...

---

<br>

# 반복문(Loops)

Loop는 반복적으로 코드를 실행해야 할 때 사용됩니다. 아래는 예제입니다:

{% note no-icon %}
{% code lang:python %}
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
for planet in planets:
print(planet, end=' ') # 같은 줄에 출력합니다. {% endcode %}
{% code %}
Mercury Venus Earth Mars Jupiter Saturn Uranus Neptune {% endcode %}
{% endnote %}

`for` 반복문에는

- 사용할 변수 이름 (이 경우 `planet`)
- 반복할 값들의 집합 (이 경우 `planets`)

"`in`" 이라는 단어를 사용하여 함께 연결합니다.

"`in`"의 오른쪽에는 반복에 사용될 수 있다면 어떠한 객체라도 올 수 있습니다. 대체적으로 어떠한 그룹으로 생각될 수만 있다면 반복문에 사용될 수 있습니다.

{% tabs loop_examples %}

<!-- tab tuple @eye -->

{% note no-icon %}
lists 외에도 tuple의 요소들을 반복 할 수도 있습니다.

{% code lang:python %}
multiplicands = (2, 2, 2, 3, 3, 5)
product = 1
for mult in multiplicands:
product = product \* mult
product {% endcode %}
{% code lang:python %}
360 {% endcode %}
{% endnote %}

<!-- endtab -->

<!-- tab string @eye -->

{% note no-icon %}
string 의 각 character 마다 반복문을 돌릴 수 있습니다.

{% code lang:python %}
s = 'steganograpHy is the practicE of conceaLing a file, message, image, or video within another fiLe, message, image, Or video.'
msg = ''

# s 문자열의 대문자들을 출력. 한번에 하나씩

for char in s:
if char.isupper():
print(char, end='') {% endcode %}
{% code lang:python %}
HELLO {% endcode %}
{% endnote %}

<!-- endtab -->

{% endtabs %}

## range()

`range()` 는 일련의 연속적인 숫자들을 반환하는 함수입니다. 이는 반복문을 작성하는데 매우 유용합니다.
예를 들어, 우리가 어떤 행동을 5번 반복하고자 한다면 아래와 같이 작성하면 됩니다:

{% note no-icon %}
{% code lang:python %}
for i in range(5):
print("Doing important work. i =", i) {% endcode %}
{% code %}
Doing important work. i = 0
Doing important work. i = 1
Doing important work. i = 2
Doing important work. i = 3
Doing important work. i = 4 {% endcode %}
{% endnote %}

## while loops

파이썬에는 또 다른 반복문으로 특정 조건을 만족할 때까지 반복하는 `while` 이 있습니다.

{% note no-icon %}
{% code lang:python %}
i = 0
while i < 10:
print(i, end=' ')
i += 1 {% endcode %}
{% code %}
0 1 2 3 4 5 6 7 8 9 {% endcode %}
{% endnote %}

`while` 반복문의 인자는 boolean 문으로 평가되고, False로 평가 될 때까지 반복문이 실행됩니다.

---

<br>

# 리스트 내포(List Comprehensions)

> 리스트 컴프리핸션 이라고 영문 그대로 읽는 경우가 더 많은 것 같습니다...

리스트 내포는 파이썬에서 가장 사랑받고 독특한 특징 중 하나입니다. 자잘한 설명보다는 그냥 몇 가지 예제들을 보는 것이 보다 이해하기 쉬울 것 같습니다.

{% tabs list_comprehensions %}

<!-- tab WITH_LC @eye -->

{% note no-icon %}
List comprehension 줄여서 LC라고 하겠습니다. `**` 은 파이썬 산술 연산자에서 제곱을 의미합니다.

{% code lang:python %}
squares = [n**2 for n in range(10)]
squares {% endcode %}
{% code lang:python %}
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81] {% endcode %}
{% endnote %}

<!-- endtab -->

<!-- tab WITHOUT_LC @eye -->

{% note no-icon %}
LC 없이 작성하면 아래와 같습니다.

{% code lang:python %}
squares = []
for n in range(10):
squares.append(n\*\*2)
squares {% endcode %}
{% code lang:python %}
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81] {% endcode %}
{% endnote %}

<!-- endtab -->

{% endtabs %}

`if` 조건을 추가 할 수도 있습니다:

{% note no-icon %}
{% code lang:python %}
short_planets = [planet for planet in planets if len(planet) < 6]
short_planets {% endcode %}
{% code lang:python %}
['Venus', 'Earth', 'Mars'] {% endcode %}
{% endnote %}

(SQL에 익숙하신 분이라면, "WHERE" 절과 비슷하다고 느끼셨을 겁니다.)
다음은 `if` 조건으로 필터링하고 loop 변수에 일부 변환을 적용하는 예제입니다:

{% tabs if_condition %}

<!-- tab SINGLE_LINE @eye -->

{% note no-icon %}
대문자로 바꾸고 뒤에 '!'를 추가합니다.

{% code lang:python %}

# str.upper() 은 모두 대문자로 변환한 string을 반환합니다

loud_short_planets = [planet.upper() + '!' for planet in planets if len(planet) < 6]
loud_short_planets {% endcode %}
{% code lang:python %}
['VENUS!', 'EARTH!', 'MARS!'] {% endcode %}
{% endnote %}

<!-- endtab -->

<!-- tab MULTI_LINE @eye -->

{% note no-icon %}
대부분의 경우 한줄로 작성하는 것을 선호하지만, 구조를 파악하기 쉽게 하기 위해 3줄로 나눠서 작성할 수도 있습니다.
(SQL과 비교하자면, 각 줄은 SELECT, FROM, WHERE로 생각할 수 있겠군요)

{% code lang:python %}
[
planet.upper() + '!'
for planet in planets
if len(planet) < 6
] {% endcode %}
{% code lang:python %}
['VENUS!', 'EARTH!', 'MARS!'] {% endcode %}
{% endnote %}

<!-- endtab -->

{% endtabs %}

표현식의 왼쪽에는 꼭 반복문의 변수를 포함할 필요가 없습니다(하지만 이런 경우는 매우 드뭅니다). 아래의 표현식이 어떤 결과를 출력할까요? "output" 탭을 눌러서 확인해 보세요.

{% tabs if_example, 1 %}

<!-- tab CODE @code -->

{% code lang:python %}
[32 for planet in planets] {% endcode %}

<!-- endtab -->

<!-- tab OUTPUT @terminal -->

{% code lang:python %}
[32, 32, 32, 32, 32, 32, 32, 32] {% endcode %}

<!-- endtab -->

{% endtabs %}

`min`, `max` 및 `sum` 과 같은 기능과 LC가 함께 사용되면 여러 줄로 작성된 코드를 한 줄의 매우 인상적인 코드로 표현할 수 있습니다.

{% tabs LC_condition %}

<!-- tab ORIGINAL_CODE @eye -->

{% note no-icon %}
예를 들어, 다음과 같이 음수의 개수를 세는 함수를 살펴보겠습니다:

{% code lang:python %}
def count_negatives(nums):
"""Return the number of negative numbers in the given list.

    >>> count_negatives([5, -1, -2, 0, 3])
    2
    """
    n_negative = 0
    for num in nums:
        if num < 0:
            n_negative = n_negative + 1
    return n_negative {% endcode %}

{% endnote %}

<!-- endtab -->

<!-- tab ONE_LINE_CODE @eye -->

{% note no-icon %}
LC를 사용하면 한 줄로 표현 가능합니다. 훨씬 보기 좋지 않은가요?

{% code lang:python %}
def count_negatives(nums):
return len([num for num in nums if num < 0]) {% endcode %}
{% endnote %}

<!-- endtab -->

<!-- tab SHORTER_CODE @eye -->

{% note no-icon %}
만약 조금이라도 더 짧은 코드를 원하신다면 다음과 같이 표현할 수도 있습니다.

{% code lang:python %}
def count_negatives(nums): # 기억하기: "booleans and conditionals" 연습문제에서, 파이썬의 별난 특징으로 # True + True + False + True 는 3으로 계산한다는 점을 응용.
return sum([num < 0 for num in nums]) {% endcode %}
{% endnote %}

<!-- endtab -->

{% endtabs %}

위 3가지 방법 중 어떤 것이 "최고의" 방법인지는 매우 주관적입니다. 보다 적은 코드로 문제를 해결하는 것이 항상 좋은 일이지만, [The Zen of Python](https://en.wikipedia.org/wiki/Zen_of_Python)에 적힌 다음 내용을 기억해 두는 것이 좋습니다.

- Readability counts. 가독성이 중요합니다.
- Explicit is better than implicit. 명확한 것이 암시적인 것보다 낫습니다.

이러한 도구들을 사용하여 읽기 쉽고 간결한 프로그램을 짜도록 합시다. 하지만 둘 중 하나를 골라야하는 상황이 온다면, 다른 사람들이 읽고 이해하기 쉬운 코드를 짜는 것을 선호하도록 합시다.

<br><br><br>

# 연습문제(Your Turn)

[loops and list comprehensions 예제](https://www.kaggle.com/kernels/fork/1275177)
