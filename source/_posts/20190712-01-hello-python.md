---
title: 01 HELLO, PYTHON!
author:
  nick: TAEJIN
  link: null
categories:
  - LANGUAGE
  - PYTHON
tags: [파이썬, 캐글, 튜토리얼, kaggle, programming language, python, language, tutorial]
date: 2019-07-12 14:11:51
subtitle: Kaggle 홈페이지 Python 강좌 참고
cover: '/img/kaggle_python.png'


---

# Reference

- Kaggle 홈페이지 - [Kaggle](https://www.kaggle.com)
- 1강 'Hello, Python' - [Python Micro-Course Home Page](https://www.kaggle.com/colinmorris/hello-python)

------



# 개요(Intro)

Data Science에 필요한 Python의 핵심적인 부분들을 배우는 과정입니다. 본 과정은 기초적인 코딩 경험이나 지식이 있는 사람들을 대상으로 작성되었습니다. (만약 코딩에 익숙하지 않으시다면  "[Python for Non-Programmers](https://wiki.python.org/moin/BeginnersGuide/NonProgrammers)" 해당 문서를 참고하는 것을 권장합니다)



우선, Python의 구문(syntax), 변수 할당(variable assignment), 산술 연산자(arithmetic operators)에 대해 가볍게 다루어 보겠습니다. 만약 Python에 경험이 있으시면 바로 연습문제([exercise with Kaggle Kernal](https://www.kaggle.com/kernels/fork/1275163))로 넘어가셔도 됩니다.

<br><br><br>

# Hello, Python!

**Python** 은 영국의 코미디 그룹 [몬티 파이선(Monty Python)](https://en.wikipedia.org/wiki/Monty_Python)에서 그 이름을 가져왔습니다. 그들에게 존경을 표하는 마음으로 우리의 첫 python 프로그램을 스팸(spam)에 관한 그들의 코미디 스케치(skit)를 만들어 볼까요?
`몬티 파이선의 코미디 스케치 25화 7분 50초부터 해당 에피소드가 등장한다고 합니다` - [youtube 영상](https://www.youtube.com/watch?v=zLih-WQwBSc)

{% tabs spam_skit, 1 %}
  <!-- tab CODE @code -->
  그저 재미로, 아래의 코드를 읽어보시고 어떻게 실행 될지 예상해 보세요.
  {% note default %}
    {% code lang:python %}
      spam_amout = 0
      print(spam_amout)

      #스팸, 계란, 스팸, 스팸, 베이컨과 스팸 주문
      spam_amout = spam_amout + 4

      if spam_amount >0:
        print("But I don't want ANY spam!")

      viking_song = "Spam " * spam_amount
      print(viking_song)
    {% endcode %}
  {% endnote %}
  <!-- endtab -->

  <!-- tab OUTPUT @terminal -->
  결과는 아래와 같습니다
  {% note success %}
    {% code %}
      0
      But I don't want ANY spam!
      Spam Spam Spam Spam
    {% endcode %}
  {% endnote %}
  <!-- endtab -->
{% endtabs %}
<br>
자, 이제 하나하나 분석해보겠습니다. 이 간단한 프로그램은  파이썬 코드가 어떻게 생겼는지, 어떻게 동작하는지를 여러 중요한 측면들을 통해 보여줍니다. 위에서 부터 순서대로 살펴보겠습니다.
<br>

```python
spam_amount = 0
```

**변수 선언** : `spam_amount`라는 변수를 만들고 할당 연산자라고하는 = 을 사용하여 0 값을 할당합니다.

> **잠깐!** :  만약 기존에 다른 언어(Java 또는 C ++ 등)로 프로그래밍을 하셨던 분의 경우 파이썬 코드에서는 몇 가지 빠져있는 것을 느꼈을 것 입니다.
>
> > `spam_amount`를 할당하기 전에 "선언(declar)"할 필요가 없습니다.
> > 우리는 파이썬에게 어떤 유형의 값인 `spam_amount`가 참조 할지를 말할 필요가 없습니다. 사실, 우리는 문자열(string)이나 부울(boolean)과 같은 다른 종류의 것을 참조하기 위해 `spam_amount`를 재할당 할 수 있습니다.

<br>

```python
print(spam_amout)  # 0
```

**함수 호출** : `print` 함수는 화면에 전달 된 값을 표시하는 파이썬 함수입니다. 함수 이름 뒤에 괄호를 넣고 그 괄호 안에 입력 (또는 인자)을 넣음으로써 함수를 호출합니다.

<br>

```python
#스팸, 계란, 스팸, 스팸, 베이컨과 스팸 주문
spam_amout = spam_amout + 4
```

첫 줄은 **주석(comment)** 입니다.파이썬에서는 `#` 기호로 시작하면 주석으로 처리합니다.

다음으로 우리는 재할당(reassignment)의 예를 볼 수 있습니다. 기존 변수의 값을 재할당하는 것은 변수를 만드는 것과 똑같은 것처럼 보입니다. <- 여전히 할당 연산자 = 을 사용합니다.

이 경우 `spam_amount`에 지정하는 값으로 이전 값에 대한 간단한 산술 연산을 한 값을 할당합니다. 파이썬은 (0 + 4 = 4)에서 `=` 오른쪽에있는 표현식의 값을 왼쪽에있는 변수에 할당합니다.

<br>

```python
if spam_amount > 0:
  print("But I don't want ANY spam!") # But I don't want ANY spam!

viking_song = "Spam Spam Spam"
print(viking_song)	#Spam Spam Spam
```

**조건문(conditional)**에 대한 설명은 나중에 자세히 다루겠지만, 코드를 전혀 짜본적 없더라도 이 문장이 어떤 것을 의미하는지는 짐작할 수 있을 것 입니다. 파이썬은 가독성과 단순성 때문에 높이 평가됩니다.

어떤 코드가 `if문`에 속해 있는지 구별하는 방법을 잘 보십시오. `"But I don't want ANY spam!"`  문자열은 `spam_amount`가 양수일 때만 출력되어야 합니다. 하지만 뒤에 `print (viking_song)`과 같은 코드는 무슨일이 있어도 실행 되어야합니다. 우리(그리고 파이썬)는 그것을 어떻게 알 수 있습니까?

`if문` 줄(line)의 끝에있는 콜론 (`:`)은 새로운 "코드 블록"이 시작되고 있음을 나타냅니다. 들여 쓰기되는 후속 행이 **해당 코드 블록의 일부** 입니다. 다른 언어에서는 `{` 중괄호 `}`를 사용하여 코드 블록의 시작과 끝을 표시합니다. Python의 이런 공백을 사용한 코드 블럭은 다른 언어에 익숙한 프로그래머에게는 놀라운 일일 수 있지만, 코드 블록의 들여 쓰기를 시행하지 않는 언어보다 일관되고 읽기 쉬운 코드가 될 수 있습니다.

이후의 행에서 `viking_song`을 다루는 줄은 여분의 4 칸으로 들여 쓰이지 않기 때문에 `if`의 코드 블록에 포함되지 않습니다. 나중에 함수를 정의하고 루프(loops)를 사용할 때 들여 쓰기 된 코드 블록의 예제를 보게 될 것입니다.

이 스니펫은(snippet)은 파이썬에서의 **문자열(string) 형태** 입니다.

```python
"But I don't want ANY spam!"
```

문자열은 <u>큰 따옴표</u> 나 <u>작은 따옴표</u>로 표시 할 수 있습니다. (예제의 문자열에는 작은 따옴표가 포함되어 있으므로 파이썬이 혼동하는 것을 방지하기 위해 큰 따옴표를 사용했습니다.)

<br>

```python
viking_song = "Spam " * spam_amount
print(viking_song)	# Spam Spam Spam Spam
```

`*`연산자는 두 개의 숫자를 곱하는데 사용되기도 하지만(`3 * 3`은 9로 계산됩니다), 문자열에 숫자를 곱하여 그 수만큼 반복되는 문자열을 만들 수도 있습니다. 파이썬에서 `*`와 `+` 같은 연산자는 어디에 적용되는지에 따라 이와 같이 많은 시간 절약 트릭을 제공합니다. (참고: [operator overloading](https://en.wikipedia.org/wiki/Operator_overloading))

<br><br>

## 파이썬에서의 수와 산술(Numbers and arithmetic in Python)

위 예제를 통해 우리는 숫자 값을 가지는 변수를 이미 보았습니다.

```python
spam_amout = 0
```

변수형(type)을 "Number" 라고 표현하기보다 좀 더 전문적인 표현을 원한다면 우리는 파이썬에게 `spam_amout` 의 type을 물어볼 수 있습니다.

```python
type(spam_amout)	# int
```

변수가 `ìnt` 형 (short for integer) 임을 알 수 있습니다. 파이썬에는 이 외에도 다른 형태의 숫자형이 있습니다

```python
type(19.95)	# float
```

`float`형은 소수점 이하의 숫자를 나타냅니다 - 가중치(weight)나 비율(proportion)을 나타낼 때 유용합니다.

`type()` 함수는 위에서 다뤘던 `print()` 함수 이후 두번째로 만나는 내장 함수이며 기억해두시면 좋습니다. 이 함수를 통해 파이썬에게 "이 함수의 형태가 무엇인지?"를 묻고 답을 얻을 수 있습니다.

<br>

숫자(number)를 다룬다면 빠질 수 없는게 산술(arithmetic)입니다. 우린 이미 `+` 더하기 연산과, `*` 곱하기 연산을 위에서 살펴 보았습니다(sort 함수). 파이썬에는 계산기에서 볼 수 있는 기본적인 연산을 지원합니다.

| Operator | Name           | Description                                        |
| :------- | :------------- | :------------------------------------------------- |
| `a + b`  | Addition       | Sum of `a` and `b`                                 |
| `a - b`  | Subtraction    | Difference of `a` and `b`                          |
| `a * b`  | Multiplication | Product of `a` and `b`                             |
| `a / b`  | True division  | Quotient of `a` and `b`                            |
| `a // b` | Floor division | Quotient of `a` and `b`, removing fractional parts |
| `a % b`  | Modulus        | Integer remainder after division of `a` by `b`     |
| `a ** b` | Exponentiation | `a` raised to the power of `b`                     |
| `-a`     | Negation       | The negative of `a`                                |

<br>

하나의 흥미로운 사실은 계산기에는 나누기 버튼이 하나만 있는 반면 파이썬에는 <u>두 가지 종류로 구분</u>되어 있습니다. "True division"이 우리에게 익숙한 기본적인 나눗셈 연산을 수행합니다.

```python
print(5 / 2)	# 2.5
print(6 / 2)	# 3.0

```

결과는 항상 `float` 형으로 반환됩니다.

<br>

`//` 연산은 나눗셈 된 값을 반올림 한 정수값을 결과로 반환합니다.

```python
print(5 // 2)	# 2
print(6 // 2)	# 3
```

위 연산이 유용하게 쓰일만한 상황이 떠오르시나요? 곧 예제를 통해 살펴보도록 하겠습니다.

<br><br>

### 연산 순서(Order of operations)

초등학교에서 다들 산술 연산의 연산 순서 대해 배우셨을겁니다. `외국에서는 PEMDAS - Parentheses, Exponents, Multiplication/Division, Addition/Subtraction 로 외우나 봅니다`  괄호 ->지수 -> 곱셈 /나눗셈 -> 덧셈 /뺄셈 순서로 계산하면 된다고 기억하실겁니다.

파이썬에서도 비슷한 규칙으로 계산을 합니다. 그리고 매우 직관적입니다.

```python
8 - 3 + 2 	# 7
-3 + 4 * 2	# 5
```

기본적인 연산만으로는 우리가 원하는 결과를 얻지 못할 경우도 생깁니다.

```python
hat_height_cm = 25
my_height_cm = 190
# How tall am I, in meters, when wearing my hat?
total_height_meters = hat_height_cm + my_height_cm / 100
print("Height in meters =", total_height_meters, "?")	# Height in meters = 26.9 ?
```

이 경우 **괄호(parentheses)**를 사용하면 되겠습니다. 괄호를 사용하면 하위 표현식(sub-expression)을 먼저 계산할 수 있도록 연산의 순서를 조절할 수 있습니다.

```python
total_height_meters = (hat_height_cm + my_height_cm) / 100
print("Height in meters =", total_height_meters) # Height in meters = 2.15
```



### 연산 관련 내장함수(Builtin functions for working with numbers)

`min`과 `max` 는 각각 최소값과 최대값을 반환합니다.

```python
print(min(1, 2, 3))	# 1
print(max(1, 2, 3))	# 3
```

`abs`는 절대값을 반환합니다.

```python
print(abs(32))	# 32
print(abs(-32))	# 32
```

`int`와 `float`를 사용해서 각자의 형태(type)로 변환이 가능합니다.

```python
print(float(10))	# 10.0
print(int(3.33))	# 3
# 심지어 문자열(string)에서도 호출 가능하다!
print(int('807') + 1)	# 808
```



<br><br><br>

# 연습문제(Your Turn)

학습한 내용을 연습해 보세요. **[first Python programming exercise](https://www.kaggle.com/kernels/fork/1275163)**

<br><br><br>
