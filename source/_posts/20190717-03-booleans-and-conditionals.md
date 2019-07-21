---
title: 03 Booleans and Conditionals
date: 2019-07-17 11:45:34
categories:
  - LANGUAGE
  - PYTHON
tags: [파이썬, 캐글, 튜토리얼, kaggle, programming language, python, language, booleans, conditionals, tutorial]
subtitle: Kaggle 홈페이지 Python 강좌 참고
---

# Reference

- Kaggle 홈페이지 - [Kaggle](https://www.kaggle.com)
- 5강 'Booleans and Conditionals' - [Python Micro-Course Home Page](https://www.kaggle.com/colinmorris/booleans-and-conditionals)

------

<br>

# 불리언(Booleans)

파이썬에는 `True`와 `False` 중 하나의 값을 가지는 `bool` 타입의 변수가 있습니다.

{% tabs bool_type %}
<!-- tab CODE @code -->
  {% code lang:python %}
  x = True
  print(x)
  print(type(x)){% endcode %}
<!-- endtab -->

<!-- tab CODE @code -->
  {% code lang:terminal %}
  True
  <class 'bool'>{% endcode %}
<!-- endtab -->
{% endtabs %}

보통 코드에 `True`나 `False` 값을 바로 넣기보다 **불리언 연산자들(boolean operators)** 를 통해 boolean 값을 얻습니다. 이 연산자들은 질문에 대한 참/거짓을 알려줍니다. 아래 표와 예제들을 통해 이 연산자들을 알아보겠습니다.

## 비교 연산자들(Comparison Operations)

| Operation | Description                   |      | Operation | Description                      |
| :-------- | :---------------------------- | :--- | :-------- | :------------------------------- |
| `a == b`  | `a` equal to `b`              |      | `a != b`  | `a` not equal to `b`             |
| `a < b`   | `a` less than `b`             |      | `a > b`   | `a` greater than `b`             |
| `a <= b`  | `a` less than or equal to `b` |      | `a >= b`  | `a` greater than or equal to `b` |


{% note info no-icon %}
  {% code lang:python %}
    def can_run_for_president(age):
        """Can someone of the given age run for president in the US?"""
        # 미국 헌법에는 35세 이상이여야 한다고 명시되어 있습니다"
        return age >= 35

    print("Can a 19-year-old run for president?", can_run_for_president(19))
    print("Can a 45-year-old run for president?", can_run_for_president(45)){% endcode %}

  {% code %}
    Can a 19-year-old run for president? False
    Can a 45-year-old run for president? True{% endcode %}
{% endnote %}

비교 연산자는 조금 영리한거 같지만...

{% note success %}
  {% code lang:python %}
  3.0 == 3{% endcode %}

  {% code %}
  True{% endcode %}
{% endnote %}

꼭 그런거 같진 않습니다...

{% note danger %}
  {% code lang:python %}
  '3' == 3{% endcode %}

  {% code %}
  False{% endcode %}
{% endnote %}

비교 연산자들이 앞서 보았던 산술 연산자들(arithmetic operators)과 더해지면 무한한 범위의 수학적 테스트들을 표현하는게 가능합니다.

{% tabs example_1, 1 %}
<!-- tab CODE @code -->
  {% note primary %}

    예를 들어, 2 로 나눈 나머지가 1 인지 확인하여 숫자가 홀수 인지를 검사할 수 있습니다.

    {% code lang:python %}
      def is_odd(n):
        return (n % 2) == 1
      print("Is 100 odd?", is_odd(100))
      print("Is -1 odd?", is_odd(-1)){% endcode %}
  {% endnote %}
<!-- endtab -->

<!-- tab OUTPUT @terminal -->
  {% note success %}
    {% code %}
      Is 100 odd? Fasle
      Is -1 odd? True{% endcode %}

    비교 연산자를 사용할 때 `=` 대신 `==` 을 사용한다는 것을 기억하십시오. 만약 `n == 2` 라고 적는 다면 n의 값을 묻는 것이고, `n = 2` 라고 적으면 n에 할당된 값을 변경하는 것입니다.
  {% endnote %}
<!-- endtab -->
{% endtabs %}


## 불리언 값 연산(Combining Boolean Values)

파이썬은 보통의 "and", "or"과 "not" 개념을 사용하여 boolean 값들을 연산하는 기능을 제공합니다. 사실 boolean 관련 파이썬 연산자들은 저게 전부입니다: `and`, `or`, `not`

이것으로 우리는 `can_run_for_president` 함수를 조금 더 정확하게 만들 수 있습니다.

{% note info no-icon %}
  {% code lang:python %}
    def can_run_for_president(age, is_natural_born_citizen):
        """Can someone of the given age and citizenship status run for president in the US?"""
        # 미국 헌법에는 미국에서 태어난 시민이고 35세 이상이여야 한다고 명시되어 있습니다"
        return is_natural_born_citizen and (age >= 35)

    print(can_run_for_president(19, True))
    print(can_run_for_president(55, False))
    print(can_run_for_president(55, True)){% endcode %}

  {% code %}
    False
    False
    True{% endcode %}
{% endnote %}

간단하게, 아래 표현식의 결과를 예상할 수 있나요?

{% tabs example_2, 1 %}
<!-- tab CODE @code -->
  {% code lang:python %}
    True or True and False{% endcode %}
<!-- endtab -->

<!-- tab ANSWER @terminal -->
  {% code %}
    True{% endcode %}
<!-- endtab -->
{% endtabs %}

파이썬에는 위와 같은 표현식에서 우선순위 규칙(precedence rule)에 따라 연산의 순서를 결정합니다. 예를 들어, `and` 는 `or` 보다 우선순위에 있기 때문에 첫번째 표현식은 참(True)이 됩니다. 만약 왼쪽에서 오른쪽으로 연산했다면 `True or True` 를 먼저 실행한 다음(결과는 `True`), 그 결과를 `False`와 `and` 연산하여 최종 값인 `False`  를 얻었을 것입니다.

우선순위([order of precedence](https://docs.python.org/3/reference/expressions.html#operator-precedence))를 외우려고 할 수도 있지만 괄호를 사용하는 것이 더 안전한 방법입니다. 이는 버그를 방지하는데 도움이 될 뿐만이 아니라 코드를 읽는 모든 사람이 이해하기 수월해 집니다.

예를 들어, 아래의 코드를 살펴보세요.

```python
prepared_for_weather = have_umbrella or rain_level < 5 and have_hood or not rain_level > 0 and is_workday
```

오늘 날씨에 ...


- 만약 우산을 가지고 있다면...
- 혹은 만약 비가 많이 오는게 아니고 내가 후드를 가지고 있다면...
- 아니면 비가 내리지 않고 일하는 날이 아니라면 준비되었는지 말해줍니다

위 파이썬 코드는 버그가 있을뿐만 아니라 읽기에도 힘듭니다. 괄호를 추가해서 두 가지의 문제점을 해결해 보겠습니다:

```python
prepared_for_weather = have_umbrella or (rain_level < 5 and have_hood) or not (rain_level > 0 and is_workday)
```

{% tabs parentheses %}
<!-- tab Single_parenthese @eye -->
  {% note primary no-icon%}
    각각 괄호로 묶어 주겠습니다.

    {% code lang:python %}
      prepared_for_weather = have_umbrella or (rain_level < 5 and have_hood) or not (rain_level > 0 and is_workday){% endcode %}
  {% endnote %}
<!-- endtab -->

<!-- tab More_parenthese @eye -->
  {% note primary no-icon%}
    가독성을 높이기 위해 괄호를 더 사용해도 좋습니다

    {% code lang:python %}
      prepared_for_weather = have_umbrella or ((rain_level < 5) and have_hood) or (not (rain_level > 0 and is_workday)){% endcode %}
  {% endnote %}
<!-- endtab -->

<!-- tab Multiple_lines @eye -->
  {% note primary no-icon%}
    혹은 위에서 언급한 3가지 조건을 강조하기 위해 여러 줄로 작성해도 됩니다.

    {% code lang:python %}
    prepared_for_weather = (
      have_umbrella
      or ((rain_level < 5) and have_hood)
      or (not (rain_level > 0 and is_workday))
    ){% endcode %}
  {% endnote %}
<!-- endtab -->
{% endtabs %}

<br><br><br>
# 조건문(Conditionals)

불리언(boolean)은 그 자체만으로도 매우 유용하지만 `if`, `elif`, `else` 키워드를 사용하는 조건문과 함께 사용되면 진가를 발휘됩니다.

조건문 혹은, `if-then` 문을 사용하면 프로그래머는 일정 불리언 조건(참/거짓 조건)에 따라 특정 코드를 실행할 수 있게 됩니다. 파이썬 조건문의 기본 예제는 다음과 같습니다.

```python
def inspect(x):
    if x == 0:
        print(x, "is zero")
    elif x > 0:
        print(x, "is positive")
    elif x < 0:
        print(x, "is negative")
    else:
        print(x, "is unlike anything I've ever seen...")

inspect(0)
inspect(-15)
```
```terminal
0 is zero
-15 is negative
```

파이썬의 `if`와 `else`는 다른 언어에서 주로 사용하는 것과 같습니다; `elif` 는 조금 독특한 키워드로 `else if` 를 축약한 단어입니다. 조건문에서 `elif` 와 `else` 는 선택사항입니다. `elif` 는 얼마든지 추가하고 싶은만큼 추가하실 수 있습니다.

콜론(`:`)과 공백을 사용하여 별도의 코드 블록을 나타내는 것을 기억하시길 바랍니다. 이는 함수를 정의 할 때와 유사합니다; 함수의 헤더는 `:`로 끝나고 다음 줄은 4칸 들여 쓰기됩니다. 모든 들여쓰기 된 줄들은 다음 <u>들여쓰기가 안된 줄</u>을 만날 때까지 하나의 함수에 속하게 됩니다.

```PYTHON
def f(x):
    if x > 0:
        print("Only printed when x is positive; x =", x)
        print("Also only printed when x is positive; x =", x)
    print("Always printed, regardless of x's value; x =", x)

f(1)
f(0)
```
```terminal
Only printed when x is positive; x = 1
Also only printed when x is positive; x = 1
Always printed, regardless of x's value; x = 1
Always printed, regardless of x's value; x = 0
```

## 불리언 변환(Boolean conversion)

우리는 앞서 int 형으로 바꿔주는 `int()` 와, float 형으로 바꾸는 `float()` 봤기 때문에, bool 형으로 바꿔주는 `bool()` 이라는 함수가 있다는 것이 별로 놀랍지 않습니다.

```PYTHON
print(bool(1)) # all numbers are treated as true, except 0
print(bool(0))
print(bool("asf")) # all strings are treated as true, except the empty string ""
print(bool(""))
# Generally empty sequences (strings, lists, and other types we've yet to see like lists and tuples)
# are "falsey" and the rest are "truthy"
```
```
True
False
True
False
```

boolean이 예상되는 조건문에서 non-boolean 객체를 사용할 수 있습니다. 파이썬은 암시적으로 그에 상응하는 boolean 값으로 처리 할 것입니다 :

```PYTHON
if 0:
    print(0)
elif "spam":
    print("spam")
```
```
spam
```

## 조건식(일명 '삼항연산(ternary)')


어떤 조건에 따라 두 개의 값 중 하나를 변수의 값으로 설정하는 것은 매우 흔한 패턴입니다.

{% note %}
  {% code lang:python %}
  def quiz_message(grade):
    if grade < 50:
        outcome = 'failed'
    else:
        outcome = 'passed'
    print('You', outcome, 'the quiz with a grade of', grade)

  quiz_message(80)
  {% endcode %}
  {% code %}
  You passed the quiz with a grade of 80
  {% endcode %}
{% endnote %}

파이썬에는 이러한 경우에 문장을 단순화 시킬 수 있는 단일 라인 조건식 구문(syntax)을 지원합니다.

{% note success %}
  {% code lang:python %}
  def quiz_message(grade):
      outcome = 'failed' if grade < 50 else 'passed'
      print('You', outcome, 'the quiz with a grade of', grade)

  quiz_message(45)
  {% endcode %}
  {% code %}
  You failed the quiz with a grade of 45
  {% endcode %}
{% endnote %}

보시면 다른 언어에 있는 삼항 연산자와 비슷하다는 것을 알 수 있습니다. 예를 들어, javascript에서 라면 우리는 위의 표현을 `var outcome = grade <50? 'failed': 'passed'` 로 작성할 것입니다. (하지만 가독성 측면에서 파이썬이 더 우수하다고 생각합니다.)


<br><br><br>
# 연습문제(Your Turn)

booleans and conditionals -> **[third Python programming exercise](https://www.kaggle.com/kernels/fork/1275165)**
