---
title: 스프링 - POJO
author:
  nick: TAEJIN
  link: null
categories:
  - WEB
  - SPRING
tags:
  - SPRING
  - POJO
date: 2019-02-04 00:59:18
subtitle: POJO에 대해서 알아보자
cover: https://spring.io/img/spring-by-pivotal.png


---

### Reference

[Plain Old Java Object-위키](https://ko.wikipedia.org/wiki/Plain_Old_Java_Object)
[POJO(Plain Old Java Object)](https://itewbm.tistory.com/entry/POJOPlain-Old-Java-Object)

------

:book: **목차** :book:

- [POJO](#pojo)
  - [POJO의 탄생](#pojo의-탄생)
  - [Enterprise JavaBean의 등장](#enterprise-javaBean의-등장)
  - [POJO 프레임워크](#pojo-프레임워크)



` 아직 많은 것을 알지 못하기 때문에 자세하고 정확한 내용은 제가 참조한 사이트나 따로 검색 또는 책을 통해 알아보는 것을 권장드립니다.`

## POJO

:heavy_check_mark: **Plain Old Java Object** : (직역) 평범한 옛날 자바 객체

 처음에 단순히 정의를 검색하다보니 정말 단순한 자바 객체인 것 같은데 왜 굳이 POJO라는 단어를 사용하는지 혼란스러웠습니다. Stack Overflow 같은데서도 자바빈과 비교하는 토론이 있기도하고 솔직히 현재도 완전히 이해했다고는 할 수 없지만 제가 생각하는 내용을 적었습니다.



##### POJO의 탄생

> Any fool can write code that a computer an understand. Good programmers write code that humans can understand.
> 컴퓨터가 이해하는 코드는 어느 바보나 짤 수 있다. 좋은 프로그래머는 사람이 이해하는 코드를 짠다.
>
> > Martin Fowler, <<리팩토링>>

<img style="float:right; height:150px;" src="https://martinfowler.com/img/mf-cologne.jpg">

 POJO는 리팩토링과 애자일 소프트웨어 개발로 유명한 영국의 소프트웨어 개발자 **마틴 파울러** 가 2000년 가을에 열렸던 어느 컨퍼런스의 발표를 준비하면서 처음 사용한 단어입니다. 그는 당시 <u>EJB(Enterprise JavaBean) 보다는 단순한 자바 오브젝트에 도메인 로직을 넣어 사용하는 것이 여러가지 장점이 있는데 왜 사람들이 EJB가 아닌 '평범한 자바 오브젝트'를 사용하기를 꺼려하하는지에 대해 의문을 가졌습니다</u> 그래서 그의 생각을 널리 알리기 위해 그는 개발자들의 심리를 이용한 기발한 전략을 세웠습니다. POJO라는 용어를 만들고 이를 기반으로한 기술을 사용한다고 발표하여 다른 개발자들에게 마치 새로운 첨단 기술인 듯한 인상을 주었습니다.
 정리하자면, 마틴 파울러는

- 자바 개발자들에게 **단순하고 평범한 자바 오브젝트 사용을 권장** 하고
- **자신의 생각을 효과적으로 전달** 하기 위해 POJO라는 단어를 사용 했습니다
  Cf) 이를 계기로 다른 분야에서도 비슷한 용어들이 생긴 것을 보면 그의 전략이 성공적이 였다는 것을 쉽게 알 수 있습니다.
  - Plain Old Data Structures(PODS) - C++ 언어에서 오직 C 언어의 특징만 사용하는 경우
  - Plain Old Documentation(POD) - 펄(Perl) 언어에서 사용
  - Plain Old PHP Object(POPO) - PHP 언어에서 사용



이제 겨우 POJO의 형체가 희미하게 보이는 것 같습니다. 이 친구를 더 자세히 알기 위해선,

- EJB(Enterprise JavaBean)는 무엇이며 어떤 문제점이 있는가
- POJO란 그럼 그저 EJB 이전의 방식으로 돌아가는 것인가
  를 알아야 겠다고 생각했습니다.



##### Enterprise JavaBean의 등장

기술이 발전하면서 자바의 기초적인 JDK만으로 복잡해져가는 기업의 비즈니스 로직을 구현하는 것은 개발자들에게 부담이 되었습니다. 이러한 문제를 해결하기 위해 EJB가 등장하였고,  **'EJB를 사용하면 개발자는 로우레벨의 기술들에 관심을 가질 필요 없이 애플리케이션 개발을 쉽게 만들 수 있다'** 라고 EJB 1.0의 스펙에서 제시 되었습니다.
 하지만 현실은 불필요할 만큼 과도한 엔지니어링으로 <u>EJB는 실패한 케이스</u>라고 많은 개발자들이 이야기합니다.

- 1% 미만의 애플리케이션에만 필요한 멀티 DB를 위한 분산 트랜잭션(무거운 JTA 기반의 글로번 트랜잭션 관리 기능)
- 고가의 WAS(CPU 당 몇 백에서 몇 천만 원) 필요
- EJB 컴포넌트는 컨테이너 밖에서는 정상적으로 동작하지 않음(많은 시간이 걸리는 수정-빌드-배표-테스트 과정 반복)
- 간단한 기능에 대해서 조차 자동화 테스트를 만드는 것이 거의 불가능
- **EJB 스텍을 따르는 비즈니스 오브젝트들은 객체지향적인 특징과 장점을 포기해야 함**

 결국 마틴 파울러와 같은 많은 오피니언 리더들은 EJB와 같은 잘못 설계된 과도한 기술을 피하고, 객체지향 원리에 따라 만들어진 자바 언어의 기본에 충실하게 비즈니스 로직을 구현하는 일명 *POJO 방식* 으로 돌아서야 한다고 지적하였습니다.



##### POJO 프레임워크

이때까지 내용을 되짚어 보면 **POJO란 결국 단순하고 기본에 충실한 자바 오브젝트로 되돌아 가는 것**인데 그렇다면 또다시 로우레벨의 API를 이용해 복잡한 코드를 작성해야 하고, 많은 기술적인 문제들을 애플리케이션 코드에 그대로 노출시켜 개발해야 한다는 문제로 돌아간다는 것이 아닌가? 하는 의문이 생길 것 입니다.
 개발자들이 비즈니스 로직에만 집중할 수 있는 애플리케이션 복잡도를 제거하는 장점은 그대로 가져가면서, 객체지향적인 설계와 자동화된 테스트의 편의성 등을 다시 회복시키기 위해 등장한 것이 바로 **POJO 기반의 프레임워크** 입니다! 가장 대표적인 프레임워크 제품으로는 *하이버네이트* 와 *스프링* 이 있습니다.

<br><br><br>
