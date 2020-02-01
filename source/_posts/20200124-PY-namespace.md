---
title: (PYTON) Namespace
date: 2020-01-24 15:39:59
categories:
  - LANGUAGE
  - PYTHON
  - TERMINOLOGY
tags: [파이썬, programming language, python, language]
subtitle: 용어 정리
---


# Reference

- 옥스포드 사전? - [lexico.com](https://www.lexico.com/definition/namespace)
- 위키피디아 '네임스페이스' - [wikipedia.org](https://en.wikipedia.org/wiki/Namespace)
- 이름공간이란? - [파이썬 프로그래밍 입문서](https://python.bakyeono.net/chapter-8-3.html)

> 개인적인 생각과 상상으로 작성한 내용들이 포함되어 있습니다

------
</br>

# Namespace?

> 생각보다 네임스페이스라는 용어를 자주 접하게 되어서 이참에 명확하게 정리해두고자 작성하게 되었습니다

{% note info %}
<strong style="color:red">NOUN</strong>
  <span style="color:green">*Computing*</span>
    A class of elements (e.g. addresses, file locations, etc.) in which each element has a name unique to that class, although it may be shared with elements in other classes.
{% endnote %}

네임스페이스는 단어 그대로 name과 space가 합쳐져 이름을 가지는 공간이라는 뜻으로 컴퓨터학에서 사용되는 용어입니다

쉽게 생각해서 어느 학교(프로그램)에 민수(객체)라는 이름을 가진 학생이 2명이 있다고 했을 때,
선생님이 그냥 "민수야 이것 좀 해봐" 라고 하면 둘 중 어느 민수를 지칭하는 건지 모릅니다
하지만 한 명의 민수는 1반에 속해있고 다른 민수는 8반에 속해있다고 하면 둘을 구분 지을 수 있습니다
여기서는 반이 네임스페이스의 역할을 한다고 볼 수 있습니다

또 다른 예시로는,
'python' 이라는 용어는 컴퓨터학에서는 __프로그래밍 언어__ 를 말하며 '파이썬'이라고 읽히지만
그리스 신화에서는 __델토이 신탁소를 지배하는 거대한 뱀__ 을 가리키며 고대 그리스어로 '피톤'이라고 읽습니다
동물사전에는 __비단 뱀__ 으로 정의됩니다 (google에서 이미지로 검색하면 비단 뱀 사진이 압도적으로 많습니다)
> 파이썬 아이콘이 뱀 모양이기도 해서 오해할 수 있지만, 파이썬 언어의 창시자 귀도 반 로썸(Guido van Rossum)은 자신이 좋아하는 영국 코미디 프로인 ‘몬티 파이선의 날아다니는 서커스(Monty Python’s Flying Circus)’에서 영감을 얻었다고 합니다

이렇게 한 단어 'python'은 여러 의미를 가지고 있는데 우리가 이들을 구분할 수 있는 이유는 무엇일까요?
본능적으로 알 수 있듯이, 'python'이 **컴퓨터** 의 네임스페이스에 있으면 __프로그래밍 언어__ 로,
**그리스 신화** 의 네임스페이스에 있다면 __거대한 뱀__ 으로, **동물사전** 이라는 네임스페이스면 __비단 뱀__ 으로
우리는 인식할 수 있습니다.


</br>

# C++에서의 Namespace

>개인적으로 저는 C언어를 처음 배울 때 잘 몰라도 그냥 `#include <stdio.h>`를 입력 했었고,
  C++를 처음 배울 때도 일단 모르겠지만 `using namespace std`를 입력 했었던 것 같습니다

{% code lang:cpp %}
  #include <iostream>

  // This is how one brings a name into the current scope.  In this case, it's
  // bringing them into global scope.
  using std::cout;
  using std::endl;

  namespace box1 {
      int box_side = 4;
  }

  namespace box2 {
      int box_side = 12;
  }

  int main() {
      int box_side = 42;
      cout << box1::box_side << endl;  // Outputs 4.
      cout << box2::box_side << endl;  // Outputs 12.
      cout << box_side << endl;  // Outputs 42.
  }   {% endcode %}

</br>

# Python에서의 Namespace

파이썬에서는 각각의 모듈(module)들이 네임스페이스 역할을 합니다.
모듈이 계층적인 패키지들에 속해있기 때문에 네임스페이스 또한 계층적인 성격을 띕니다.

- 예를 들어, 2개의 함수 func1()과 func2() 그리고 1개의 클래스 class1을 가지는 모듈이 있다고 가정해 봅시다
  모듈을 전체를 import하면 함수와 클래스 모두 잘 작동하는 것을 볼 수 있습니다
{% code lang:python %}
  # assume module a defines two functions : func1() and func2() and one class : class1
  import modulea

  modulea.func1()
  modulea.func2()
  a = modulea.class1()  {% endcode %}


- 하지만 모듈 내의 특정한 함수만 import하면 현제 작업하고 있는 네임스페이스에는 func2() 함수와 class1이 없는 것으로 인식됩니다
{% code lang:python %}
  # assume modulea defines two functions : func1() and func2() and one class : class1
  from modulea import func1

  func1()
  func2() # this will fail as an undefined name, as will the full name modulea.func2()
  a = class1() # this will fail as an undefined name, as will the full name modulea.class1()  {% endcode %}


- 간혹 모듈의 이름이 너무 길어서 짧게 쓰고 싶을 때, `import ... as ...` 를 통해 임의로 이름을 바꿀 수 있습니다
{% code lang:python %}
  import numpy as np
  a = np.arange(1000)  {% endcode %}
