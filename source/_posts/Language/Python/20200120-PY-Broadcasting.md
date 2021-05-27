---
title: (PYTHON) Numpy - Broadcasting
date: 2020-01-20 22:19:41
categories:
  - LANGUAGE 🚀
  - PYTHON
  - TERMINOLOGY
tags: [파이썬, programming language, python, language]
subtitle: 용어 정리
---

# Reference

- Broadcasting, 브로드캐스팅- [정보통신기술용어해설](http://www.ktword.co.kr/word/abbr_view.php?m_temp1=629)
- Broadcasting arrays in Numpy - [Eli Bendersky's website](https://eli.thegreenplace.net/2015/broadcasting-arrays-in-numpy/)
- Array Broadcasting in NumPy - [SciPy.org](https://docs.scipy.org/doc/numpy/user/theory.broadcasting.html#array-broadcasting-in-numpy)

- The foundation of scientific python - [oreilly.com](https://www.oreilly.com/library/view/elegant-scipy/9781491922927/ch01.html)

---

# Numpy

## broadcasting

흔히 방송과 관련해서 '브로드캐스트(broadcast)'라는 용어를 자주 들었을 것 입니다.
**'TV나 신문과 같은 전송매체를 통해 대중에게 정보를 전송하는 행위'** 라고 일반적으로 정의합니다.
혹은 네트워크 과목을 배우셨으면 유니캐스트(unicast), 멀티캐스트(multicast)를 같이 떠올리시며
**단일 노드로부터 해당 네트워크의 모든 노드에게 패킷/프레임을 전파하는 것** 으로 이해하실 수 있습니다.

![broadcast](https://www.researchgate.net/profile/Rosangela_Penteado/publication/280610232/figure/fig7/AS:267926301311009@1440890016756/0-Broadcast-multicast-and-unicast-interactions.png)

Python의 Numpy 패키지에서는 해당 용어를 조금 다르게 정의합니다.

{% note info %}
"Broadcasting is the process of making arrays to have compatible shapes for arithmetic operations."

Broadcasting은 **서로 다른 구조(shape)를 가진 배열의 산술 연산이 가능하도록 차원을 맞춰주는 것** 을 말합니다.
{% endnote %}

아시다 싶이 행렬의 덧셈과 뺄셈은 각 행렬이 같은 구조일 때만 가능합니다.
행렬의 곱셈에서는 앞 행렬의 열(column)의 수와 뒷 행렬의 행(row)의 수가 같으면 연산이 가능합니다.

아래 예제는 3-차원 벡터 2개의 곱셈을 연산하는 코드로 아무런 문제 없이 결과값이 출력되는 것을 볼 수 있습니다.

{% code lang:python %}
from numpy import array
a = array([1.0, 2.0, 3.0])
b = array([2.0, 2.0, 2.0])
a \* b

# output

# array([ 2., 4., 6.])

{% endcode %}

하지만 만약 3-차원 벡터와 스칼라 값의 곱셈을 연산하는 코드를 실행하면 어떻게 될까요?

{% code lang:python %}
from numpy import array
a = array([1.0, 2.0, 3.0])
b = 2.0
a \* b

# output

# array([ 2., 4., 6.])

{% endcode %}

이 또한 별 문제 없이 정상적으로 결과값을 출력한다는 것을 볼 수 있습니다.

행렬의 연산은 같은 크기(차원)일 때만 가능한데
위 코드가 정상적으로 동작한다는 것을 보니 내부적으로 연산을 위해 스칼라 값을 같은 차원의 벡터 값으로 변환했다는 것을 유추할 수 있습니다.
즉, Numpy에서는 브로드캐스팅을 통해 두 행렬 간 연산이 가능하도록 아래 그림과 같이 상대적으로 작은 행렬의 차원(크기)을 큰 행렬과 맞춰주는 것 입니다.

![figure1](https://docs.scipy.org/doc/numpy/_images/theory.broadcast_1.gif)

## broadcasting rule

<span style="color:red">그렇다고 이 브로드캐스팅이 만능인 것은 아닙니다.</span>
최소한의 조건은 만족해야 동작하는데 이러한 조건을 **broadcasting rule** 이라고 합니다.

{% note info %}
"In order to broadcast, the size of the trailing axes for both arrays in an operation must either be the same size or one of them must be one."

Broadcasting이 허용되려면, 각 행의 크기(차원)가 같거나 둘 중 하나라도 1이면 됩니다.
{% endnote %}

정의만으로는 이해가 잘 안되지만 몇 가지 예제를 보시면 매우 간단하다는 것을 깨닫게 될 것입니다.

{% note success %}
| | | |
|:---------:|:---------------------------:|------------------------------------:|
| A </br> B | (2d array) </br> (1d array) | 4 x 3 </br> &emsp;&nbsp; 3 |
| Result | (2d array) | 4 x 3 |
| A </br> B | (2d array) </br> (1d array) | 4 x 3 </br> &emsp;&nbsp; 1 |
| Result | (2d array) | 4 x 3 |
| A </br> B | (4d array) </br> (3d array) | 8 x 1 x 6 x 1 </br> &emsp;&nbsp; 7 x 1 x 5 |
| Result | (4d array) | 8 x 7 x 6 x 5 |
| A </br> B | (3d array) </br> (3d array) | 15 x 3 x 5 </br> &emsp;&emsp; 3 x 1|
| Result | (3d array) | 15 x 3 x 5 |
{% endnote %}

{% note danger %}
| | | |
|:---------:|:---------------------------:|------------------------------------:|
| A </br> B | (1d array) </br> (1d array) | 3 </br> 4 |
| Result | error | error |
| A </br> B | (3d array) </br> (2d array) | 8 x 4 x 3 </br> &emsp;&nbsp; 2 x 1 |
| Result | error | error |
{% endnote %}

![figure2](https://docs.scipy.org/doc/numpy/_images/theory.broadcast_2.gif)

![figure2](https://docs.scipy.org/doc/numpy/_images/theory.broadcast_3.gif)

![figure2](https://docs.scipy.org/doc/numpy/_images/theory.broadcast_4.gif)

{% code lang:python %}
from numpy import array
a = array([[0.0,  0.0,  0.0],
              [10.0, 10.0, 10.0],
              [20.0, 20.0, 20.0],
              [30.0, 30.0, 30.0]])
b = array([1.0, 2.0, 3.0])
a + b

# output

# array([[ 1., 2., 3.],

# [ 11., 12., 13.],

# [ 21., 22., 23.],

# [ 31., 32., 33.]])

{% endcode %}

{% code lang:python %}
from numpy import array, newaxis
a = array([0.0, 10.0, 20.0, 30.0])
b = array([1.0, 2.0, 3.0])
a[:,newaxis] + b

# output

# array([[ 1., 2., 3.],

# [ 11., 12., 13.],

# [ 21., 22., 23.],

# [ 31., 32., 33.]])

{% endcode %}

---

# N-dimensional arrays

Numpy에서 차원에 따라 axis가 조금씩 헷갈리기 때문에 그림을 잘 기억하도록 하자

![dimensional arrays](https://www.oreilly.com/library/view/elegant-scipy/9781491922927/assets/elsp_0105.png)
