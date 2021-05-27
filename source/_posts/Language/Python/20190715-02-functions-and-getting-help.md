---
title: (파이썬) 02 Functions and Getting Help
categories:
  - LANGUAGE 🚀
  - PYTHON
  - KAGGLE
tags: [파이썬, 캐글, 튜토리얼, kaggle, programming language, python, language, functions, tutorial]
date: 2019-07-15 15:06:03
subtitle: Kaggle 홈페이지 Python 강좌 참고
---

# Reference

- Kaggle 홈페이지 - [Kaggle](https://www.kaggle.com)
- 3강 'Functions and Getting Help' - [Python Micro-Course Home Page](https://www.kaggle.com/colinmorris/functions-and-getting-help)

---

# 개요(Intro)

앞서 `print` 나 `abs` 와 같은 함수를 사용해 보았습니다. 파이썬에는 이 외에도 수 많은 내장 함수들을 가지고 있고 자신만의 함수를 정의하여 사용할 수도 있습니다.

이번 강에서는 함수를 정의하고 사용하는 방법에 대해 배워보겠습니다.

<br><br><br>

# 도움말 활용(Getting Help)

만약 `abs` 함수의 기능이 무엇인지 잊어버렸다면 어떻게 하시겠습니까?

`help()`함수는 아마 파이썬 함수 중에서도 가장 중요한 함수일 것입니다. `help()`함수의 정확한 사용법을 알게 된다면 대부분의 다른 함수들을 이해하는 열쇠를 쥐고 있는 것과 다름 없습니다.

{% tabs First unique name, 1 %}

  <!-- tab CODE @code -->

{% note default %}
**예제**,
{% code lang:python %}
help(round)
{% endcode %}
{% endnote %}

  <!-- endtab -->

  <!-- tab OUTPUT @terminal -->

{% note success %}
**출력**,
{% code %}
Help on built-in function round in module builtins:

      round(...)
          round(number[, ndigits]) -> number

          Round a number to a given precision in decimal digits (default 0 digits).
          This returns an int when called with one argument, otherwise the
          same type as the number. ndigits may be negative.
    {% endcode %}

    `help()`함수는 2 가지를 보여줍니다:

    1. 해당 함수의 헤더 `round(number[, ndigits])`. 이 경우 `round()` 함수가 `number`로 설정한 인자를 취한다는 것을 알 수 있습니다. 또한 사용자는 선택적으로 `ndigits`로 설정된 별도의 인자를 제공 할 수 있습니다.

    2. 해당 함수의 기능에 대한 (영어)설명

{% endnote %}

   <!-- endtab -->

{% endtabs %}

{% note danger %}

**<span style="color:red">Common pitfall(흔히하는 실수)</span>**

함수(function)를 찾을 때 함수의 이름을 전달해야하며 함수를 호출 한 결과는 전달하지 말아야합니다.

{% endnote %}

{% tabs pitfall, 1 %}

  <!-- tab CODE @code -->

What happens if we invoke help on a call to the function abs()?
{% note default %}
**결과를 확인해 보세요->**
{% code lang:python %}
help(round(-2.01))
{% endcode %}
{% endnote %}

  <!-- endtab -->

  <!-- tab OUTPUT @terminal -->

{% note danger %}
**원하던 결과가 아님**
{% code %}
Help on int object:

    class int(object)
     |  int(x=0) -> integer
     |  int(x, base=10) -> integer
     |
     |  Convert a number or string to an integer, or return 0 if no arguments
     |  are given.  If x is a number, return x.__int__().  For floating point
     |  numbers, this truncates towards zero.
     |
     |  If x is not a number or if base is given, then x must be a string,
     |  bytes, or bytearray instance representing an integer literal in the
     |  given base.  The literal can be preceded by '+' or '-' and be surrounded
     |  by whitespace.  The base defaults to 10.  Valid bases are 0 and 2-36.
     |  Base 0 means to interpret the base from the string as an integer literal.
     |  >>> int('0b100', base=0)
     |  4
     |
     |  Methods defined here:
     |
     |  __abs__(self, /)
     |      abs(self)
     |
     |  __add__(self, value, /)
     |      Return self+value.
     |
     |  __and__(self, value, /)
     |      Return self&value.
     |
     |  __bool__(self, /)
     |      self != 0
     |
     |  __ceil__(...)
     |      Ceiling of an Integral returns itself.
     |
     |  __divmod__(self, value, /)
     |      Return divmod(self, value).
     |
     |  __eq__(self, value, /)
     |      Return self==value.
     |
     |  __float__(self, /)
     |      float(self)
     |
     |  __floor__(...)
     |      Flooring an Integral returns itself.
     |
     |  __floordiv__(self, value, /)
     |      Return self//value.
     |
     |  __format__(...)
     |      default object formatter
     |
     |  __ge__(self, value, /)
     |      Return self>=value.
     |
     |  __getattribute__(self, name, /)
     |      Return getattr(self, name).
     |
     |  __getnewargs__(...)
     |
     |  __gt__(self, value, /)
     |      Return self>value.
     |
     |  __hash__(self, /)
     |      Return hash(self).
     |
     |  __index__(self, /)
     |      Return self converted to an integer, if self is suitable for use as an index into a list.
     |
     |  __int__(self, /)
     |      int(self)
     |
     |  __invert__(self, /)
     |      ~self
     |
     |  __le__(self, value, /)
     |      Return self<=value.
     |
     |  __lshift__(self, value, /)
     |      Return self<<value.
     |
     |  __lt__(self, value, /)
     |      Return self<value.
     |
     |  __mod__(self, value, /)
     |      Return self%value.
     |
     |  __mul__(self, value, /)
     |      Return self*value.
     |
     |  __ne__(self, value, /)
     |      Return self!=value.
     |
     |  __neg__(self, /)
     |      -self
     |
     |  __new__(*args, **kwargs) from builtins.type
     |      Create and return a new object.  See help(type) for accurate signature.
     |
     |  __or__(self, value, /)
     |      Return self|value.
     |
     |  __pos__(self, /)
     |      +self
     |
     |  __pow__(self, value, mod=None, /)
     |      Return pow(self, value, mod).
     |
     |  __radd__(self, value, /)
     |      Return value+self.
     |
     |  __rand__(self, value, /)
     |      Return value&self.
     |
     |  __rdivmod__(self, value, /)
     |      Return divmod(value, self).
     |
     |  __repr__(self, /)
     |      Return repr(self).
     |
     |  __rfloordiv__(self, value, /)
     |      Return value//self.
     |
     |  __rlshift__(self, value, /)
     |      Return value<<self.
     |
     |  __rmod__(self, value, /)
     |      Return value%self.
     |
     |  __rmul__(self, value, /)
     |      Return value*self.
     |
     |  __ror__(self, value, /)
     |      Return value|self.
     |
     |  __round__(...)
     |      Rounding an Integral returns itself.
     |      Rounding with an ndigits argument also returns an integer.
     |
     |  __rpow__(self, value, mod=None, /)
     |      Return pow(value, self, mod).
     |
     |  __rrshift__(self, value, /)
     |      Return value>>self.
     |
     |  __rshift__(self, value, /)
     |      Return self>>value.
     |
     |  __rsub__(self, value, /)
     |      Return value-self.
     |
     |  __rtruediv__(self, value, /)
     |      Return value/self.
     |
     |  __rxor__(self, value, /)
     |      Return value^self.
     |
     |  __sizeof__(...)
     |      Returns size in memory, in bytes
     |
     |  __str__(self, /)
     |      Return str(self).
     |
     |  __sub__(self, value, /)
     |      Return self-value.
     |
     |  __truediv__(self, value, /)
     |      Return self/value.
     |
     |  __trunc__(...)
     |      Truncating an Integral returns itself.
     |
     |  __xor__(self, value, /)
     |      Return self^value.
     |
     |  bit_length(...)
     |      int.bit_length() -> int
     |
     |      Number of bits necessary to represent self in binary.
     |      >>> bin(37)
     |      '0b100101'
     |      >>> (37).bit_length()
     |      6
     |
     |  conjugate(...)
     |      Returns self, the complex conjugate of any int.
     |
     |  from_bytes(...) from builtins.type
     |      int.from_bytes(bytes, byteorder, *, signed=False) -> int
     |
     |      Return the integer represented by the given array of bytes.
     |
     |      The bytes argument must be a bytes-like object (e.g. bytes or bytearray).
     |
     |      The byteorder argument determines the byte order used to represent the
     |      integer.  If byteorder is 'big', the most significant byte is at the
     |      beginning of the byte array.  If byteorder is 'little', the most
     |      significant byte is at the end of the byte array.  To request the native
     |      byte order of the host system, use `sys.byteorder' as the byte order value.
     |
     |      The signed keyword-only argument indicates whether two's complement is
     |      used to represent the integer.
     |
     |  to_bytes(...)
     |      int.to_bytes(length, byteorder, *, signed=False) -> bytes
     |
     |      Return an array of bytes representing an integer.
     |
     |      The integer is represented using length bytes.  An OverflowError is
     |      raised if the integer is not representable with the given number of
     |      bytes.
     |
     |      The byteorder argument determines the byte order used to represent the
     |      integer.  If byteorder is 'big', the most significant byte is at the
     |      beginning of the byte array.  If byteorder is 'little', the most
     |      significant byte is at the end of the byte array.  To request the native
     |      byte order of the host system, use `sys.byteorder' as the byte order value.
     |
     |      The signed keyword-only argument determines whether two's complement is
     |      used to represent the integer.  If signed is False and a negative integer
     |      is given, an OverflowError is raised.
     |
     |  ----------------------------------------------------------------------
     |  Data descriptors defined here:
     |
     |  denominator
     |      the denominator of a rational number in lowest terms
     |
     |  imag
     |      the imaginary part of a complex number
     |
     |  numerator
     |      the numerator of a rational number in lowest terms
     |
     |  real
     |      the real part of a complex number

    {% endcode %}

{% endnote %}\*

   <!-- endtab -->

{% endtabs %}

파이썬 내부에서는 다음과 같이 표현식을 해석합니다. 먼저 `round(-2.01)` 값을 계산한 다음 해당 표현식의 결과에 대한 도움말(help)을 제공합니다.

(도움말(OUTPUT)을 보면 `integer` 에 대해 참 많은 설명이 있습니다. 나중에 파이썬에서 객체, 메소드, 속성에 관해 배우고나면 위의 방대한 도움말 출력이 더 잘 이해가 될 것입니다.)

`round`는 짧은 docstring을 가진 매우 간단한 함수입니다. `help`는 `print` 함수와 같이 보다 복잡하고 다양한 기능을 가진 함수를 다룰 때 더 많은 도움을 줍니다. 다음 출력 결과가 지금은 이해가지 않아도 걱정하지 마세요... 지금은 이 도움말에서 새로운 점이 있는지 확인만 하셔도 됩니다.

{% code lang:python %}
help(print)
{% endcode %}
{% code lang:python%}
Help on built-in function print in module builtins:

print(...)
print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)

      Prints the values to a stream, or to sys.stdout by default.
      Optional keyword arguments:
      file:  a file-like object (stream); defaults to the current sys.stdout.
      sep:   string inserted between values, default a space.
      end:   string appended after the last value, default a newline.
      flush: whether to forcibly flush the stream.

{% endcode %}

뭔가 발견하셨나요? 예를 들어 print가 `sep`라는 인자를 취할 수 있다는 것을 알 수 있습니다. 그리고 설명을 통해 인자들 사이에 넣는 문자열이라는 것을 알 수 있습니다.

## 함수정의(Defining functions)

내장 함수(builtin function)는 훌륭하지만, 상황에 따라 나만의 함수가 필요하기도 합니다. 아래의 간단한 예제를 살펴보겠습니다.

{% code lang:python%}
def least_difference(a, b, c):
diff1 = abs(a - b)
diff2 = abs(b - c)
diff3 = abs(a - c)
return min(diff1, diff2, diff3)
{% endcode %}

이 코드는 `a`, `b`와 `c`라는 세 개의 매개변수를 취하는 `least_difference`라는 함수를 생성합니다.

함수는 `def` 라는 키워드의 헤더로 시작합니다. `:` 다음에 들여쓰기 된 코드 블록(즉, 2번째 줄부터)은 함수가 호출 될 때 실행됩니다.

`return`은 함수와 관련된 또다른 고유한 키워드입니다. 파이썬에서 `return` 문을 만나면 함수를 즉시 종료하고 (return의)오른쪽에있는 값을 전달합니다.

`least_difference()`가 어떤 기능을 하는지 아시겠나요? 확실하지 않은 경우 몇 가지 예를 통해 언제든지 시도해 볼 수 있습니다.

{% tabs df_examples %}

  <!-- tab EXAMPLE 1 @eye-->

{% note info%}
**함수에 인자를 넣어서 확인해 볼 수 있습니다**
{% code lang:python %}
print(
least_difference(1, 10, 100),
least_difference(1, 10, 10),
least_difference(5, 6, 7), # Python allows trailing commas in argument lists. How nice is that?
)
{% endcode %}
{% endnote %}
{% note success %}
{% code %}
9 0 1
{% endcode %}
{% endnote %}

  <!-- endtab -->

  <!-- tab EXAMPLE 2 @eye-->

{% note info%}
**혹은 `help()` 함수를 사용해서 설명을 읽어볼 수 있습니다**
{% code lang:python %}
help(least_difference)
{% endcode %}
{% endnote %}
{% note warning %}
{% code %}
Help on function least_difference in module **main**:

      least_difference(a, b, c)
    {% endcode %}
    아쉽게도 파이썬은 제가 작성한 코드를 읽고 설명을 작성할 만큼 똑똑하지 못한 것을 볼 수 있습니다.하지만 우리는 함수를 작성하며 이 함수에 대한 설명을 추가할 수 있습니다. 이를 <b>docstring</b> 이라고 합니다

{% endnote %}

  <!-- endtab -->

{% endtabs %}

### Docstring

{% tabs docstring, 1 %}

  <!-- tab CODE @code -->

{% note primary %}
{% code lang:python %}
def least_difference(a, b, c):
"""Return the smallest difference between any two numbers
among a, b and c.

        >>> least_difference(1, 5, -5)
        4
        """
        diff1 = abs(a - b)
        diff2 = abs(b - c)
        diff3 = abs(a - c)
        return min(diff1, diff2, diff3)

    {% endcode %}

    docstring은 함수 바로 뒤에 삼중 따옴표 `"""`로 묶인 문자열(여러 줄로 작성 가능)입니다. 이 함수에 대한 `help()`를 호출하면 docstring이 표시됩니다.

{% endnote %}

  <!-- endtab -->

  <!-- tab OUTPUT @terminal -->

{% note default %}
{% code %}
help(least_difference)
{% endcode %}

    {% code %}
    Help on function least_difference in module __main__:

    least_difference(a, b, c)
      Return the smallest difference between any two numbers
      among a, b and c.

      >>> least_difference(1, 5, -5)
      4
    {% endcode %}

{% endnote %}

{% note info %}
**<span style="color=blue">참고</span>**
docstring의 마지막 두 줄은 예제 함수의 호출과 결과입니다.
(`>>>`는 파이썬 대화형 셸(interactive shells)에서 사용되는 명령 프롬프트에 대한 참조입니다.) 파이썬은 예제 호출을 실행하지 않습니다.
이는 독자의 이익을 위해서입니다. 함수의 docstring에 보편적으로 하나 이상의 예제 호출을 포함하지 않지만, 설명을 읽는 사람이 함수의 기능을 이해하도록 돕는 데 매우 효과적 일 수 있습니다.
실제 예를 보려면 numpy 함수 [np.eye에 대한 설명서](https://github.com/numpy/numpy/blob/v1.14.2/numpy/lib/twodim_base.py#L140-L194)를 참조하십시오.
{% endnote %}

  <!-- endtab -->

{% endtabs %}

훌륭한 프로그래머들은 docstring을 사용합니다. 만약 그 코드를 사용하고 버릴 계획이 아니라면 말이죠(이는 드문 경우입니다).
여러분도 docstring을 작성하는 습관을 들이시길 바랍니다.

## 반환값이 없는 함수들(Functions that don't return)

만약 우리가 작성한 함수(function)에 `return` 키워드를 작성하지 않으면 어떻게 될까요?

{% tabs return_example, 1 %}

  <!-- tab CODE @code -->

{% code lang:python %}
def least_difference(a, b, c):
"""Return the smallest difference between any two numbers
among a, b and c.
"""
diff1 = abs(a - b)
diff2 = abs(b - c)
diff3 = abs(a - c)
min(diff1, diff2, diff3)

      print(
        least_difference(1, 10, 100),
        least_difference(1, 10, 10),
        least_difference(5, 6, 7),
      )

{% endcode %}

  <!-- endtab -->

  <!-- tab OUTPUT @terminal -->

{% code %}
None None None
{% endcode %}

파이썬은 그러한 함수 정의를 허용합니다. 그 함수들의 호출 한 결과는 `None`이라는 특별한 값을 가집니다. (이는 다른 언어의 "null"개념과 유사합니다.)

`return` 문이 없으면 `least_difference` 는 완전히 무의미해 보이지만 이 함수를 통해 아무 것도 반환하지 않고 유용한 작업을 수행 할 수 있습니다.
우리는 이러한 함수를 2개나 봤습니다: `print()`와 `help()`함수는 아무 것도 반환하지 않았습니다.
우리는 함수들의 부작용(side effect - 화면에 텍스트를 넣는 것)을 위해서만 호출합니다. 유용한 부작용의 다른 예는 파일에 쓰거나 입력을 수정하는 것을 포함합니다.

{% subtabs mystery %}
<!-- tab CODE @code -->
{% code lang:python %}
mystery = print()
print(mystery)
{% endcode %}
<!-- endtab -->

    <!-- tab OUTPUT @terminal -->
      {% code %}
        None
      {% endcode %}
    <!-- endtab -->

{% endsubtabs %}

  <!-- endtab -->

{% endtabs %}

## 기본 매개변수(Default arguments)

`help(print)` 를 호출하면 `print` 함수에는 몇 가지의 선택적 매개변수들(optinal arguments)이 있는 것을 볼 수 있습니다.
예를 들어, 출력하고자 하는 값들 사이에 우리가 원하는 특별한 `sep` 값을 지정할 수 있습니다.

{% code lang:python %}
print(1, 2, 3, sep=' < ')
{% endcode %}

{% code %}
1 < 2 < 3
{% endcode %}

만약 특정한 값을 명시하지 않으면, `sep` 에는 기본값인 `' '`(공백) 이 들어갑니다.

{% code lang:python %}
print(1, 2, 3)
{% endcode %}

{% code %}
1 2 3
{% endcode %}

우리가 정의한 함수에 선택적 매개변수를 기본값으로 추가하는 것은 꽤 간단합니다.

{% code lang:python %}
def greet(who="Colin"):
print("Hello,", who)

greet()
greet(who="Kaggle")

# (In this case, we don't need to specify the name of the argument, because it's unambiguous.)

greet("world")
{% endcode %}

{% code %}
Hello, colin
Hello, Kaggle
Hello, world
{% endcode %}

## 함수들에 적용되는 함수들(Functions Applied to Functions)

처음에는 매우 추상적이라고 느낄 수 있지만 매우 매우 유용한 기술이 있습니다.
함수는 다른 함수의 매개변수로 사용될 수 있습니다. 몇 가지 예를 들어 보면 다음과 같습니다.

{% tabs functions_example %}

<!-- tab EXAMPLE 1 @eye -->

{% subtabs squared_call %}

  <!-- tab CODE @code -->

    {% note primary %}
      {% code lang:python %}
        def mult_by_five(x):
          return 5 * x

        def call(fn, arg):
          """Call fn on arg"""
          return fn(arg)

        def squared_call(fn, arg):
          """Call fn on the result of calling fn on arg"""
          return fn(fn(arg))

        print(
          call(mult_by_five, 1),
          squared_call(mult_by_five, 1),
          sep='\n', # '\n' is the newline character - it starts a new line
        )
      {% endcode %}
    {% endnote %}

  <!-- endtab -->

  <!-- tab OUTPUT @terminal -->

{% note success %}
{% code %}
5
25
{% endcode %}

    다른 함수에서 작동하는 함수를 "Higher order function"이라고합니다.
    아마 지금 당장은 잘 사용하지 않으시겠지만 파이썬에 내장된 매우 유용한 고차 함수들(higher order function)이 있습니다.

{% endnote %}

  <!-- endtab -->

{% endsubtabs %}

<!-- endtab -->

<!-- tab EXAMPLE 2 @eye -->

{% subtabs max %}

  <!-- tab CODE @code -->

{% note primary %}
`max` 함수에 대한 흥미로운 예제입니다,

    {% code lang:python %}
      def mod_5(x):
        """Return the remainder of x after dividing by 5"""
        return x % 5

      print(
        'Which number is biggest?',
        max(100, 51, 14),
        'Which number is the biggest modulo 5?',
        max(100, 51, 14, key=mod_5),
        sep='\n',
      )
    {% endcode %}

{% endnote %}

  <!-- endtab -->

  <!-- tab OUTPUT @terminal -->

{% note success %}
{% code %}
Which number is biggest?
100
Which number is the biggest modulo 5?
14
{% endcode %}

    기본적으로 `max` 함수는 가장 큰 인수를 반환합니다.
    그러나 선택적 `key` 인자를 사용하여 함수를 전달하면 `key(x)` (일명 'argmax')를 최대화하는 인자 `x`를 반환합니다.

{% endnote %}

  <!-- endtab -->

{% endsubtabs %}

<!-- endtab -->

{% endtabs %}

<br><br><br>

# 연습문제(Your Turn)

함수(Function)는 파이썬 프로그래밍의 새로운 세상을 열어줍니다. **[second Python programming exercise](https://www.kaggle.com/kernels/fork/1275158)**
