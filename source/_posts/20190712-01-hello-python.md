---
title: 01 HELLO, PYTHON!
author:
  nick: TAEJIN
  link: null
categories:
  - LANGUAGE
  - PYTHON
tags:
  - python
  - language
  - 파이썬
  - 언어
date: 2019-07-12 14:11:51
subtitle: Kaggle 홈페이지 Python 강좌 참고
cover: '/img/kaggle_python.png'

---

### Reference

- Kaggle 홈페이지 - [Kaggle](https://www.kaggle.com)
- 1강 'Hello, Python' - [Python Micro-Course Home Page](https://www.kaggle.com/colinmorris/hello-python)

------

:book: **목차** :book:

- [Intro](#intro)
- [Hello, Python!](#hello-python)
- [Your Turn](#your-turn)

------



### Intro

Data Science에 필요한 Python의 핵심적인 부분들을 배우는 과정입니다. 본 과정은 기초적인 코딩 경험이나 지식이 있는 사람들을 대상으로 작성되었습니다. (만약 코딩에 익숙하지 않으시다면  "[Python for Non-Programmers](https://wiki.python.org/moin/BeginnersGuide/NonProgrammers)" 해당 문서를 참고하는 것을 권장합니다)



우선, Python의 구문(syntax), 변수 할당(variable assignment), 산술 연산자(arithmetic operators)에 대해 가볍게 다루어 보겠습니다. 만약 Python에 경험이 있으시면 바로 연습문제([exercise with Kaggle Kernal](https://www.kaggle.com/kernels/fork/1275163))로 넘어가셔도 됩니다.



### Hello, Python!

**Python** 은 영국의 코미디 그룹 [몬티 파이선(Monty Python)](https://en.wikipedia.org/wiki/Monty_Python)에서 그 이름을 가져왔습니다. 그들에게 존경을 표하며 우리의 첫 python 프로그램을 스팸(spam)에 관한 그들의 코미디 스케치(skit)를 만들어 볼까요?
`몬티 파이선의 코미디 스케치 25화 7분 50초부터 해당 에피소드가 등장한다고 합니다` - [youtube 영상](https://www.youtube.com/watch?v=zLih-WQwBSc)



그저 재미로, 아래의 코드를 읽어보시고 어떻게 실행 될지 예상해 보세요.

```python
spam_amout = 0
print(spam_amout)

#스팸, 계란, 스팸, 스팸, 베이컨과 스팸 주문
spam_amout = spam_amout + 4

if spam_amount >0:
  print("But I don't want ANY spam!")

viking_song = "Spam " * spam_amount
print(viking_song)
```



결과는 아래와 같습니다

```
0
But I don't want ANY spam!
Spam Spam Spam Spam
```



자, 이제 하나하나 분석해보겠습니다. 이 간단한 프로그램은  파이썬 코드가 어떻게 생겼는지, 어떻게 동작하는지를 여러 중요한 측면들을 통해 보여줍니다. 위에서 부터 순서대로 살펴보겠습니다.

```python
spam_amount = 0
```





### Your Turn
