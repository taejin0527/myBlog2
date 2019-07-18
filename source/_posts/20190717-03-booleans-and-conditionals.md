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



<br><br><br>
# 조건문(Conditionals)


<br><br><br>
# 연습문제(Your Turn)

booleans and conditionals -> **[third Python programming exercise](https://www.kaggle.com/kernels/fork/1275165)**
