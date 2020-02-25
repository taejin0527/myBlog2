---
title: (PYTON) is 와 == 의 차이?
date: 2020-01-31 15:02:07
categories:
  - LANGUAGE
  - PYTHON
  - TERMINOLOGY
tags: [파이썬, programming language, python, language]
subtitle: 용어 정리
---

# Reference

- Is there a difference between “==” and “is”? - [stackoverflow.com](https://stackoverflow.com/questions/132988/is-there-a-difference-between-and-is)
- The difference between 'is' and '==' in Python - [dbader.org](https://dbader.org/blog/difference-between-is-and-equals-in-python)
- Python Operators - [programiz.com](https://www.programiz.com/python-programming/operators)
- 페이스ID vs 일란성쌍둥이 - [sisajournal.com](https://www.sisajournal.com/news/articleView.html?idxno=171991)


> 개인적인 생각과 상상으로 작성한 내용들이 포함되어 있습니다

------
</br>

{% note info %}
이메일로 받아보는 [🐍PyTricks]에서 `is` 와 `==` 의 차이점에 대한 내용이 있길래 정리했습니다
아래 코드의 출력값이 본인의 예상과 다르거나 혹은 이해가 안 된다면 이번 기회에 확실히 짚고 넘어갑시다
  {% code lang:python %}
    >>> a = [1, 2, 3]
    >>> b = a

    >>> a is b
    True
    >>> a == b
    True  {% endcode %}

  "is" vs "==" (위 아래의 차이점을 아시겠나요?)

  {% code lang:python %}
    # a = [1, 2, 3]
    >>> c = list(a)

    >>> a is c
    False
    >>> a == c
    True  {% endcode %}
{% endnote %}

</br>

# Operators in Python

> 둘의 차이점을 알아보기 전에 Python의 연산자들에는 어떤 것들이 있는지 큰 틀만 알아보겠습니다
> 자세한 내용은 다음에 기회가 있으면 정리하겠습니다

{% code lang:python %}
>>> x + y
9
{% endcode %}

- 여기서 `x`와 `y`는 __피연산자(operand)__ 라고 부르고 그 사이 `+`가 __연산자(operator)__ 가 됩니다
  위 예제의 덧셈 연산자 외에도 파이썬에는 다양한 연산자들이 존재합니다


{% note primary %}
  ## Python Operators

  - **Arithmetic operators**
    - `+`, `-`, `*`, `/`, `%`, `//`, `**`  
  - <strong style="color:blue">Comparison operators</strong>
    - `>`, `<`, `==`, `!=`, `>=`, `<=`
  - **Logical(Boolean) operators**
    - `and`, `or`, `not`
  - **Bitwise operators**
    - `&`, `|`, `~`, `^`, `>>`, `<<`
  - **Assignment operators**
    - `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `//=`, `**=`, `&=`, `|=`, `^=`, `>>=`, `<<=`
  - **Special operators** (Python에서 제공하는 특별한 연산자들)
    - <strong style="color:blue">Identity operators</strong>
      - `is`, `is not`
    - **Membership operators**
      - `in`, `not in`
{% endnote %}

</br>

# Equality Comparison Operators

Python에서는 같음을 비교(equality comparison)할 때 `==`와 `is` 2가지 연산자(operator)를 사용할 수 있습니다
결론부터 이야기하면 두 연사자의 차이점은 **Equality** 와 **Identity** 의 비교라는 것 입니다

요즘 최신 스마트폰은 대부분 '페이스ID' 기능을 제공하고 있습니다.
이전의 '터치ID'의 인식 오류 확률인 1/50000 보다 20배 성능이 뛰어난 1/1000000의 확률로 훨씬 보안이 뛰어나다고 알려져 있습니다
하지만 정말 똑같이 생긴 일란성 쌍둥이가 있을 때 페이스ID의 보안은 쉽게 뚫리지 않을까 하는 의구심이 들지 않나요?

쉽게 생각해서 페이스ID의 원리는 스마트폰에 등록된 얼굴 데이터와 카메라, 적외선 센서 등으로 입력되는 데이터를 비교하는 것 입니다
일란성 쌍둥이가 너무 똑같이 생겨서 입력되는 데이터 값이 거의 똑같다면 이론상 페이스ID로 서로의 스마트폰 잠금을 해제할 수 있을 것 입니다
이처럼 두 데이터가 같은 값(value)을 가지는지 비교하는 것을 **Equality comparison** 이라고 합니다

하지만 아무리 일란성 쌍둥이라고 해도 두 사람은 엄밀히 다른 사람입니다
간단하게는 주민등록 번호 등으로 구분할 수 있고, 한쪽만 가지고 있는 점이나 흉터 등과 같은 차별적인 특징으로도 구분할 수 있을 것 입니다
각 사람마다의 고유성(Identity)을 구분하는 것을 **Identity comparison** 이라고 합니다

파이썬에서 두 피연산자들의 데이터 혹은 값이 같은지를 비교하고 싶을 때, `==` 연산자를 사용하고
고유값(파이썬에서는 객체마다 고유한 상수 'id'값을 가집니다)을 비교하고 싶을 때, `is` 연산자를 사용합니다

## 동등성 Equality `==`

- 피연산자들의 **데이터/값(value)** 이 같은지를 비교합니다

{% code lang:python %}
  >>> a = [1, 2, 3]
  >>> b = a

  >>> a is b
  True
  >>> a == b
  True  {% endcode %}



## 동일성 Identity `is`

- 피연산자들의 **주소/고유한 상수(ID)** 가 같은지 비교합니다

> `id()` 의 반환값이 실제 메모리상의 주소는 아닙니다
> 하지만 해당 객체를 가리키는 유일한 상수입니다

{% code lang:python %}
  # a = [1, 2, 3]
  >>> c = list(a)

  >>> a is c
  False
  >>> a == c
  True  {% endcode %}

- `is` 연산자는 객체(object)의 id값을 `==` 연산자로 확인하는 것이라고 생각하시면 됩니다

{% code lang:python %}
  >>> a is c
  False
  >>> id(a) == id(c)
  False  {% endcode %}

</br>

# 결론

`is` 연산자는 다음 2가지 상황에서만 사용하는 것을 권장

- 피연산자들이 **같은 객체** 인지 확인할 때
- 객체가 `True`, `False`, `None` 와 같은 파이썬 상수와 비교할 때

---
---
