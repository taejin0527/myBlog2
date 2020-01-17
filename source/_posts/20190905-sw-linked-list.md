---
title: (파이썬 S/W 문제해결 기본) Linked List - 5108번 5110번
date: 2019-09-05 16:10:07
categories: SW 아카데미
tags: [삼성, 파이썬, SW Academy, python, linked list]
subtitle: (Programming Intermediate) 파이썬 S/W 문제해결 기본 7일차
---

# 5108번 - 숫자 추가

{% note %}
- 시간 : 10개 테스트케이스를 합쳐서 Python의 경우 2초
- 메모리 : 힙, 정적 메모리 합쳐서 256MB 이내, 스택 메모리 1MB 이내
{% endnote %}

> list.insert(self, index, object) 함수를 사용하여 쉽게 리스트의 해당 인덱스에 숫자 삽입

{% note success %}
{% code lang:python %}
def addNum(m):
    for _ in range(M):
        # 추가할 인덱스와 숫자 입력
        idx, num = map(int, input().split())
        mySeq.insert(idx, num)


def printNum(l):
    return mySeq[l]


T = int(input())

for test_case in range(1, T+1):
    # 수열의 길이 N, 추가 횟수 M, 출력할 인덱스 번호 L
    N, M, L = map(int, input().split())
    mySeq = [int(num) for num in input().split()]

    addNum(M)
    ans = printNum(L)

    print('#{} {}'.format(test_case, ans))
{% endcode %}
{% endnote %}

------

# 5110번 - 수열 합치기

{% note %}
- 시간 : 10개 테스트케이스를 합쳐서 Python의 경우 2초
- 메모리 : 힙, 정적 메모리 합쳐서 256MB 이내, 스택 메모리 1MB 이내
{% endnote %}

> 단순 리스트를 그대로 사용할 경우 테스트 케이스 10개 중 9개만 통과하고 1개는 제한시간 초과가 뜬다

{% note danger %}
{% code lang:python %}
def mergeSeqLists():
    finalSeq = []

    finalSeq.extend(myLists[0])

    for idx in range(1, M):
        ptr = len(finalSeq)
        for i, num in enumerate(finalSeq):
            if myLists[idx][0] < num:
                ptr = i
                break

        finalSeq = finalSeq[:ptr] + myLists[idx] + finalSeq[ptr:]

    return finalSeq


T = int(input())

for test_case in range(1, T+1):
    # 수열의 길이 N, 수열의 개수 M
    N, M = map(int, input().split())
    # 전체 수열을 저장할 리스트
    myLists = [[int(num) for num in input().split()] for _ in range(M)]

    ans = mergeSeqLists()

    print('#{} '.format(test_case), end='')
    print(' '.join(str(n) for n in ans[-1:-11:-1]))
    #print('#{} {}'.format(test_case, ans[:10]))
{% endcode %}
{% endnote %}

> 연결 리스트(Linked list)를 사용하여 성능을 끌어올리자

{% note success %}
{% code lang:python %}

{% endcode %}
{% endnote %}

------

# 5120번 - 암호

{% note %}
- 시간 : 10개 테스트케이스를 합쳐서 Python의 경우 2초
- 메모리 : 힙, 정적 메모리 합쳐서 256MB 이내, 스택 메모리 1MB 이내
{% endnote %}

>

{% note success %}
{% code lang:python %}

{% endcode %}
{% endnote %}

------

# 5122번 - 수열 편집

{% note %}
- 시간 : 10개 테스트케이스를 합쳐서 Python의 경우 2초
- 메모리 : 힙, 정적 메모리 합쳐서 256MB 이내, 스택 메모리 1MB 이내
{% endnote %}

>

{% note success %}
{% code lang:python %}

{% endcode %}
{% endnote %}

------
