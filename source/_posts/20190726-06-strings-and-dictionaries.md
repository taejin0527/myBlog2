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

{% note warning %}
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
| `\n`             |              | `"1\n2 3"`                | `1`<br> `2` `3`        |

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
print(triplequoted_hello == hello) {% endcode %}
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

문자열(string)은 연속된 문자들(characters)로 생각할 수 있습니다. 우리가 list로 할 수 있는 거의 모든 것을 문자열에서도 할 수 있습니다.

{% tabs example_string %}
<!-- tab Indexing @eye -->
{% note no-icon %}
  {% code lang:python %}
  # Indexing
  planet = 'Pluto'
  planet[0] {% endcode %}
  {% code %}
  'P' {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab Slicing @eye -->
{% note no-icon %}
  {% code lang:python %}
  # Slicing
  planet[-3:] {% endcode %}
  {% code %}
  'uto' {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab Length @eye -->
{% note no-icon %}
  {% code lang:python %}
  # How long is this string?
  len(planet)  {% endcode %}
  {% code %}
  5 {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab Loop @eye -->
{% note no-icon %}
  {% code lang:python %}
  # Yes, we can even loop over them
  [char+'! ' for char in planet]  {% endcode %}
  {% code %}
  ['P! ', 'l! ', 'u! ', 't! ', 'o! '] {% endcode %}
{% endnote %}
<!-- endtab -->
{% endtabs %}

하지만 list와 가장 큰 차이점은 문자열은 불변(immutable)이라는 점입니다. 우리는 문자열을 수정할 수 없습니다.

{% note danger %}
{% code lang:python %}
planet[0] = 'B'
# planet.append doesn't work either {% endcode %}
{% code lang:python %}
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-12-6ca42463b9f9> in <module>()
----> 1 planet[0] = 'B'
      2 # planet.append doesn't work either

TypeError: 'str' object does not support item assignment  {% endcode %}
{% endnote %}

## 문자열 메소드(String methods)

`list` 처럼, `str` 타입에는 매우 유용한 메소드들일 많이 있습니다. 몇 가지 예시를 보여드리겠습니다.

```python
  claim = "Pluto is a planet!"
```

{% tabs example_string_methods %}
<!-- tab UpperCase @eye -->
{% note no-icon %}
  {% code lang:python %}
  # 모두 대문자
  claim.upper() {% endcode %}
  {% code %}
  'PLUTO IS A PLANET!' {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab LowerCase @eye -->
{% note no-icon %}
  {% code lang:python %}
  # 모두 소문자
  claim.lower() {% endcode %}
  {% code %}
  'pluto is a planet!' {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab Index @eye -->
{% note no-icon %}
  {% code lang:python %}
  # substring의 첫번째 인덱스 값
  claim.index('plan') {% endcode %}
  {% code %}
  11 {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab Startswith @eye -->
{% note no-icon %}
  {% code lang:python %}
  claim.startswith(planet)  {% endcode %}
  {% code %}
  True {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab Endswith @eye -->
{% note no-icon %}
  {% code lang:python %}
  claim.endswith('dwarf planet')  {% endcode %}
  {% code %}
  False {% endcode %}
{% endnote %}
<!-- endtab -->
{% endtabs %}

### Going between strings and lists: .split() and .join()

`str.split()` 은 하나의 문자열을 공백 문자를 기준으로 분리한 작은 문자들로 이루어진 list로 바꿔 줍니다. 이는 하나의 큰 문자열을 단어 하나하나로 나눈 list로 바꾸는데 매우 유용합니다.

{% tabs example_split %}
<!-- tab Default @eye -->
{% note no-icon %}
  {% code lang:python %}
  words = claim.split()
  words  {% endcode %}
  {% code %}
  ['Pluto', 'is', 'a', 'planet!'] {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab Custom @eye -->
{% note no-icon %}
때로는 공백 이외의 다른 것을 기준으로 나눠야 할 때도 있습니다.

{% code lang:python %}
datestr = '1956-01-31'
year, month, day = datestr.split('-') {% endcode %}

year, month, day은 이제 각각 1956, 01, 31을 참조할 것입니다.
{% endnote %}
<!-- endtab -->
{% endtabs %}

`str.join()` 은 반대의 기능을 한다고 보시면 됩니다, seperator(분리자)로 분리되었던 문자(열) list를 하나의 긴 문자열로 묶어줍니다.

{% tabs example_join %}
<!-- tab Basic @eye -->
{% note no-icon %}
  {% code lang:python %}
  '/'.join([month, day, year]) {% endcode %}
  {% code %}
  '01/31/1956' {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab Unicode @eye -->
{% note no-icon %}
  문자열 리터럴에 유니코드 문자를 넣을 수 도 있습니다 :)
  {% code lang:python %}
  ' 👏 '.join([word.upper() for word in words]) {% endcode %}
  {% code %}
  'PLUTO 👏 IS 👏 A 👏 PLANET!' {% endcode %}
{% endnote %}
<!-- endtab -->
{% endtabs %}


### Building strings with .format()

파이썬에서는 `+` 연산자를 사용해서 문자열을 합칠 수 있습니다.

{% note no-icon %}
{% code lang:python %}
planet + ', we miss you.' {% endcode %}
{% code %}
'Pluto, we miss you.' {% endcode %}
{% endnote %}

{% note warning %}
문자열이 아닌 객체를 사용할 때는 `str()` 을 먼저 호출하여 문자열로 바꿔줘야 하는 점을 주의하셔야 합니다.

{% code lang:python %}
position = 9
planet + ", you'll always be the " + position + "th planet to me." {% endcode %}
{% code lang:python %}
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-23-73295f9638cc> in <module>()
      1 position = 9
----> 2 planet + ", you'll always be the " + position + "th planet to me."

TypeError: must be str, not int {% endcode %}
{% endnote %}

{% note no-icon %}
{% code lang:python %}
planet + ", you'll always be the " + str(position) + "th planet to me." {% endcode %}
{% code %}
"Pluto, you'll always be the 9th planet to me." {% endcode %}
{% endnote %}

가독성이 떨어지고 일일이 타입을 확인하며 바꿔줘야하는게 귀찮을 것 같습니다. `str.format()` 을 사용하면 이를 해결할 수 있습니다.

{% note no-icon %}
{% code lang:python %}
"{}, you'll always be the {}th planet to me.".format(planet, position) {% endcode %}
{% code %}
"Pluto, you'll always be the 9th planet to me." {% endcode %}
{% endnote %}

훨씬 깔끔한 것 같습니다! "format string"에 `.format()` 을 호출하고, 우리가 삽입하고자 하는 파이썬 값은 `{}` 로 표현되는 placeholder에 들어갈 것 입니다.
우리가 int형인 `position` 을 변환하기 위해 `str()` 을 호출 할 필요가 없었던 점에 주목하십시오. `format()` 에서 이를 알아서 처리합니다.
이게 `format()` 이 하는 일의 전부라해도 우리는 이를 매우 유용하게 사용할 것 입니다. 하지만 알아갈 수록 이 함수로 할 수 있는게 훨씬 더 많다는 것을 깨닫게 될 것 입니다. 조금만 더 알아보겠습니다.

{% tabs example_format %}
<!-- tab Example_1 @eye -->
{% note no-icon %}
  {% code lang:python %}
  pluto_mass = 1.303 * 10**22
  earth_mass = 5.9722 * 10**24
  population = 52910390
  #         2 decimal points   3 decimal points, format as percent     separate with commas
  "{} weighs about {:.2} kilograms ({:.3%} of Earth's mass). It is home to {:,} Plutonians.".format(
      planet, pluto_mass, pluto_mass / earth_mass, population,
  ) {% endcode %}
  {% code %}
  "Pluto weighs about 1.3e+22 kilograms (0.218% of Earth's mass). It is home to 52,910,390 Plutonians." {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab Example_2 @eye -->
{% note no-icon %}
  문자열 리터럴에 유니코드 문자를 넣을 수 도 있습니다 :)
  {% code lang:python %}
  # Referring to format() arguments by index, starting from 0
  s = """Pluto's a {0}.
  No, it's a {1}.
  {0}!
  {1}!""".format('planet', 'dwarf planet')
  print(s) {% endcode %}
  {% code %}
  Pluto's a planet.
  No, it's a dwarf planet.
  planet!
  dwarf planet! {% endcode %}
{% endnote %}
<!-- endtab -->
{% endtabs %}

조금 과장하자면 `str.format` 에 대한 설명과 내용으로 짧은 책을 쓸 수도 있기 때문에 가볍게 알아보는 본 강의에서는 이쯤에서 멈추겠습니다.
더 자세히 알고 싶으신 분은 [pyformat.info](https://pyformat.info/)와 [the offical docs](https://docs.python.org/3/library/string.html#formatstrings) 를 읽어 보시길 바랍니다.

-----

# 딕셔너리(Dictionaries)

딕셔너리(Dictionary)는 키(Key)를 값(Value)에 매핑(mapping)하기 위한 파이썬에 내장된 데이터 구조입니다.

{% note no-icon %}
{% code lang:python %}
numbers = {'one':1, 'two':2, 'three':3} {% endcode %}
이 경우, 'one', 'two'와 'three'가 key가 되고, 1, 2와 3은 해당 value입니다.
{% endnote %}

{% tabs dictionaries %}
<!-- tab Index -->
value는 list 및 string과 유사하게 대괄호 구문을 사용하여 액세스됩니다.
{% note no-icon %}
{% code lang:python %}
numbers['one']  {% endcode %}
{% code lang:python %}
1 {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab Add -->
똑같은 방식을 사용하여 다른 key, value 쌍을 추가 할 수 있습니다.
{% note no-icon %}
{% code lang:python %}
numbers['eleven'] = 11
numbers {% endcode %}
{% code lang:python %}
{'one': 1, 'two': 2, 'three': 3, 'eleven': 11} {% endcode %}
{% endnote %}
<!-- endtab -->

<!-- tab Change -->
혹은 존재하는 key의 value를 수정 할 수도 있습니다.
{% note no-icon %}
{% code lang:python %}
numbers['one'] = 'Pluto'
numbers {% endcode %}
{% code lang:python %}
{'one': 'Pluto', 'two': 2, 'three': 3, 'eleven': 11} {% endcode %}
{% endnote %}
<!-- endtab -->
{% endtabs %}

이전 강좌에서 봤던 list 내포처럼 파이썬은 dictionary 내포를 지원합니다.
{% note no-icon %}
{% code lang:python %}
planets = ['Mercury', 'Venus', 'Earth', 'Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']
planet_to_initial = {planet: planet[0] for planet in planets}
planet_to_initial {% endcode %}
{% code lang:python %}
{'Mercury': 'M',
 'Venus': 'V',
 'Earth': 'E',
 'Mars': 'M',
 'Jupiter': 'J',
 'Saturn': 'S',
 'Uranus': 'U',
 'Neptune': 'N'} {% endcode %}
{% endnote %}

`in` 연산자를 사용하여 우리는 dicionary에 어떠한 key가 존재하는지 알아볼 수 있습니다.
{% note no-icon %}
{% code lang:python %}
'Saturn' in planet_to_initial
'Betelgeuse' in planet_to_initial {% endcode %}
{% code lang:python %}
True
False {% endcode %}
{% endnote %}

dictionary 에서의 for 반복문은 해당 key들을 반복합니다.
{% note no-icon %}
{% code lang:python %}
for k in numbers:
    print("{} = {}".format(k, numbers[k])) {% endcode %}
{% code lang:python %}
one = Pluto
two = 2
three = 3
eleven = 11 {% endcode %}
{% endnote %}

`dict.keys()` 및 `dict.values​​()` 를 사용하여 모든 key 또는 모든 value들에 각각 액세스 할 수 있습니다.
{% note no-icon %}
{% code lang:python %}
# 각 행성의 초성을 가져와, 알파벳순으로 정렬하고, 각 사이에 빈칸을 넣은 string
' '.join(sorted(planet_to_initial.values())) {% endcode %}
{% code lang:python %}
'E J M M N S U V' {% endcode %}
{% endnote %}

보다 유용한 `dict.items()` 메소드는 dictionary의 key와 value를 동시에 반복 할 수있게 해줍니다. (파이썬에서는 **item** 은 곧 key와 value 쌍을 뜻합니다)
{% note no-icon %}
{% code lang:python %}
for planet, initial in planet_to_initial.items():
    print("{} begins with \"{}\"".format(planet.rjust(10), initial)) {% endcode %}
{% code lang:python %}
Mercury begins with "M"
  Venus begins with "V"
  Earth begins with "E"
   Mars begins with "M"
Jupiter begins with "J"
 Saturn begins with "S"
 Uranus begins with "U"
Neptune begins with "N" {% endcode %}
{% endnote %}

dictionary의 method 전체 목록이 궁금하시면 아래의 "help(dict)"버튼을 클릭하여 전체 도움말 페이지를 읽거나 [공식 온라인 문서](https://docs.python.org/3/library/stdtypes.html#dict)를 확인하십시오.

{% spoiler help(dict) %}
{% code %}
  Help on class dict in module builtins:

class dict(object)
 |  dict() -> new empty dictionary
 |  dict(mapping) -> new dictionary initialized from a mapping object's
 |      (key, value) pairs
 |  dict(iterable) -> new dictionary initialized as if via:
 |      d = {}
 |      for k, v in iterable:
 |          d[k] = v
 |  dict(**kwargs) -> new dictionary initialized with the name=value pairs
 |      in the keyword argument list.  For example:  dict(one=1, two=2)
 |  
 |  Methods defined here:
 |  
 |  __contains__(self, key, /)
 |      True if D has a key k, else False.
 |  
 |  __delitem__(self, key, /)
 |      Delete self[key].
 |  
 |  __eq__(self, value, /)
 |      Return self==value.
 |  
 |  __ge__(self, value, /)
 |      Return self>=value.
 |  
 |  __getattribute__(self, name, /)
 |      Return getattr(self, name).
 |  
 |  __getitem__(...)
 |      x.__getitem__(y) <==> x[y]
 |  
 |  __gt__(self, value, /)
 |      Return self>value.
 |  
 |  __init__(self, /, *args, **kwargs)
 |      Initialize self.  See help(type(self)) for accurate signature.
 |  
 |  __iter__(self, /)
 |      Implement iter(self).
 |  
 |  __le__(self, value, /)
 |      Return self<=value.
 |  
 |  __len__(self, /)
 |      Return len(self).
 |  
 |  __lt__(self, value, /)
 |      Return self<value.
 |  
 |  __ne__(self, value, /)
 |      Return self!=value.
 |  
 |  __new__(*args, **kwargs) from builtins.type
 |      Create and return a new object.  See help(type) for accurate signature.
 |  
 |  __repr__(self, /)
 |      Return repr(self).
 |  
 |  __setitem__(self, key, value, /)
 |      Set self[key] to value.
 |  
 |  __sizeof__(...)
 |      D.__sizeof__() -> size of D in memory, in bytes
 |  
 |  clear(...)
 |      D.clear() -> None.  Remove all items from D.
 |  
 |  copy(...)
 |      D.copy() -> a shallow copy of D
 |  
 |  fromkeys(iterable, value=None, /) from builtins.type
 |      Returns a new dict with keys from iterable and values equal to value.
 |  
 |  get(...)
 |      D.get(k[,d]) -> D[k] if k in D, else d.  d defaults to None.
 |  
 |  items(...)
 |      D.items() -> a set-like object providing a view on D's items
 |  
 |  keys(...)
 |      D.keys() -> a set-like object providing a view on D's keys
 |  
 |  pop(...)
 |      D.pop(k[,d]) -> v, remove specified key and return the corresponding value.
 |      If key is not found, d is returned if given, otherwise KeyError is raised
 |  
 |  popitem(...)
 |      D.popitem() -> (k, v), remove and return some (key, value) pair as a
 |      2-tuple; but raise KeyError if D is empty.
 |  
 |  setdefault(...)
 |      D.setdefault(k[,d]) -> D.get(k,d), also set D[k]=d if k not in D
 |  
 |  update(...)
 |      D.update([E, ]**F) -> None.  Update D from dict/iterable E and F.
 |      If E is present and has a .keys() method, then does:  for k in E: D[k] = E[k]
 |      If E is present and lacks a .keys() method, then does:  for k, v in E: D[k] = v
 |      In either case, this is followed by: for k in F:  D[k] = F[k]
 |  
 |  values(...)
 |      D.values() -> an object providing a view on D's values
 |  
 |  ----------------------------------------------------------------------
 |  Data and other attributes defined here:
 |  
 |  __hash__ = None
{% endcode %}
{% endspoiler %}

-----

<br><br><br>
# 연습문제(Your Turn)

[strings and dictionaries 예제](https://www.kaggle.com/kernels/fork/1275185)
