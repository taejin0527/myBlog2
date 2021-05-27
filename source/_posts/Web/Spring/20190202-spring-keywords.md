---
title: 스프링 프레임워크 핵심 개념
author:
  nick: TAEJIN
  link: null
categories:
  - WEB 🌏
  - SPRING
tags:
  - SPRING
date: 2019-02-02 15:16:10
subtitle: 스프링 프레임워크의 핵심 기술
cover: https://spring.io/img/spring-by-pivotal.png
---

### Reference

[Spring의 시작, 프레임워크의 구성요소와 동작원리](https://asfirstalways.tistory.com/334)
[스프링 프레임워크 핵심](https://scroogy.atlassian.net/wiki/spaces/SPRING/pages/1114310)

**POJO**
[스프링 프레임워크 1 - POJO에 대하여](https://limmmee.tistory.com/8)
[POJO vs JavaBeans](https://www.geeksforgeeks.org/pojo-vs-java-beans/)
[Understanding : POJO](https://spring.io/understanding/POJO)

**IoC/DI**
[스프링 프레임워크 2 - 컨테이너와 IoC](https://limmmee.tistory.com/13?category=654011)
[Spring 프레임워크 소개와 IoC 및 Spring IoC의 개념](http://wiki.javajigi.net/pages/viewpage.action?pageId=3664)
[세 가지 DI 컨테이너로 향하는 저녁 산책](www.nextree.co.kr/p11247/)
[스프링이 도대체 뭐란 말인가?](http://springmvc.egloos.com/487497)

---

## 핵심 개념들

- 스프링 프레임워크를 공부하면서 자주 언급되고 매우 중요하다고 생각하는 용어들을 정리했습니다
- 아직 많은 것을 알지 못하기 때문에 자세하고 정확한 내용은 제가 참조한 사이트나 따로 검색 또는 책을 통해 알아보는 것을 권장드립니다.

![spring triangle](https://dhsim86.github.io/static/assets/img/blog/web/2017-11-18-toby_spring_08_what_is_spring//00.png)

---

### POJO

이해가 어려우신 분들은 간략히,

- 스프링 프레임워크를 사용하면 **POJO로 애플리케이션을 만들고 엔터프라이즈 서비스를 비침투적으로 POJO에 적용할 수 있다**
- **모든 JavaBeans는 POJO 이지만, 모든 POJO는 JavaBeans가 아니다**

![pojo&javabean](https://cdncontribute.geeksforgeeks.org/wp-content/uploads/pojo.jpg)

이 정도만 숙지하고 넘어가셔도 상관 없을 것 같습니다.

:heavy_check_mark: **Plain Old Java Object** : (직역) 평범한 옛날 자바 객체

더 자세한 내용은 다른 포스트에서 다루겠지만, 간략히 스프링 공식 홈페이지에서는 POJO를 다음과 같이 소개합니다.

> By using plain old Java objects, your code is much more simplified, which lends to better testing, flexibility, and ability to change technical decisions at future stages based on knowledge and shifting requirements.

POJO를 사용함으로써,

- 코드가 간결해져서 테스트하기 편해지고 (비즈니스 로직과 특정 환결/로우 레벨 종속적인 코드를 분리함)
  쉽게 말해 인터페이스, 상속이 없는 것
- 유연해서 객체지향적 설계의 자유료운 사용이 가능

**POJO 기반의 프레임워크 == 스프링 프레임워크**

많은 POJO 프레임워크가 있고 하이버네이트와 스프링이 대표적이라고 할 수 있습니다. (이 둘의 차이점은 굳이 자세히 알아보지는 않겠습니다.) 스프링 프레임워크가 <u>많은 POJO 프레임워크 제품 중 하나</u>라는 정도로 알고 넘어가셔도 좋습니다.

**진정한 POJO 프로그래밍**

<u>자바의 객체지향적인 특징을 살려 비즈니스 로직에 충실한 개발이 가능하도록 하는 것이 진정한 POJO 프로그래밍</u>이라고 할 수 있습니다. 마치 자바를 처음 배울 때 흔히 하는 실수로, 개발은 자바로 하지만 실제로는 C 언어를 배우며 익숙해진 절차지향 방식으로 구현하는 것을 생각하시면 되겠습니다. 따라서 POJO 프레임워크 제품을 사용한다고 해서 자동으로 POJO 형식의 개발을 하고 있다고 할 수 없음을 인지하고 계셔야 합니다.

- 객체지향적인 설계원칙에 충실하도록 개발되어 있는지
- 테스트 코드 개발의 용이성이나 테스트 코드를 잘 작성했는지

를 잘 확인하시면서 POJO 프로그래밍의 장점을 잘 살려 스프링 프레임워크의 활용도를 극대화하려고 노력해야 할 것 같습니다.

---

### IoC / DI

개인적으로 재밌었던 표현이라 그대로 참조한 블로그[스프링이 도대체 뭐란 말인가?](http://springmvc.egloos.com/487497)(꼭 읽어보면 좋을 것 같습니다)의 표현을 그대로 인용하자면, 간략하게 이 둘을 **"대신 해줌(IoC)"** 과 **"미리 찜해 놓음(DI)"** 이라고 설명하였습니다.
**정신 나간듯 언제 사용될 지도 모르는 코드를 쳐대면서(IoC) 동시에 사용하고 있는 코드가 뭔지도 모르면서 일단 갖다 쓰는(DI) 획기적이고 진보적인 프로그래밍 작성 방식** 으로 IoC/DI의 개념을 표현하였고 어려우시면 이 정도로 이해하고 일단 넘어가시는 것도 좋을 것 같습니다.

![ioc](https://img1.daumcdn.net/thumb/R720x0.q80/?scode=mtistory&fname=http%3A%2F%2Fcfile10.uf.tistory.com%2Fimage%2F252FCF3B5231689B17B553)

:heavy_check_mark: **Inversion of Control** : 제어의 역전

- **제어권(Control)**
  : 자바 객체의 생성, 생명주기 관리, 객체간의 의존관계를 연결시키는 등의 행위에 대한 권한

- 객체에 대한 제어 권한이 바뀌는 것 즉, 제어 권한을 다른 대상에게 위임하는 것이라는 의미 (개발자 -> 컨테이너)
- 프레임워크에서 개발자는 필요한 부분을 개발해서 "조립"하는 방식을 취하는데, 이렇게 조립된 코드의 최종 호출은 <u>개발자에 의해서 제어되는 것이 아니라 프레임워크 내부 동작 원리에 따라 이루어짐</u>. 이를 **제어의 역전** 이라고 표현
- 스프링 프레임워크에서 지원하는 IoC Container는 POJO의 생명주기를 관리, 생성된 인스턴트들에게 추가적인 기능들을 제공
  cf) 라이브러리 vs 프레임워크 --> IoC의 개념이 적용되었나의 차이

:heavy_check_mark: **Dependency Injection** : 의존성 주입

- **의존성(Dependency)**
  : 현재 객체가 다른 객체와 상호작용(참조)하고 있다면, 다른 객체들을 현재 객체의 의존 이라고 표현

- **DI는 스프링 프레임워크에서 지원하는 IoC의 형태**

- DI는 <u>클래스 사이의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동적으로 연결</u>

  예시)

  **_Ioc/DI 가 적용되지 않은 경우_**

![instance](http://www.nextree.co.kr/content/images/2016/09/yrkim-140701-framework-02.png)

```java
package kr.co.study;

public class Foo
{
    private Bar bar;

    public Foo(){
        bar = new SubBar();	//Bar 인터페이스를 구현하는 구체적인 클래스 SubBar로 초기화
    }
}
```

​ **_Ioc/DI 가 적용되지 않은 경우_**

![inject](http://www.nextree.co.kr/content/images/2016/09/yrkim-140701-framework-03.png)

```html
//Container
<beans>
	<bean id="bar" class="kr.co.study.SubBar">
    <bean id="foo" class="kr.co.study.Foo">
        <property name="bar" ref="bar"/>		<!-- 사용할 객체들을 컨테이너에 등록 -->
    </bean>
</beans>
```

```java
//application code
package kr.co.study;

public class Foo
{
    private Bar bar;

    public void setBar(Bar bar){	//사용할 객체를 매겨변수로 받아와 동적으로 의존관계를 설정
        this.bar = bar;				//Bar 인터페이스를 구현하는 구체적인 클래스 이름이 등장하지 않음
    }
}
```

- 마틴 파울러가 그의 저서인 'Inversion of Control Containers and the Dependency Injection pattern'에서 세가지 DI 패턴을 제시
  - setter() 메소드를 이용한 의존성 삽입(Setter Injection)
  - 생성자를 이용한 의존성 삽입 (Constructor Injection)
  - 초기화 인터페이스를 이용한 의존성 삽입(Interface Injection)

<br>
- 스프링 프레임워크에서의 DI 패턴
  1. XML을 통한 의존성 주입
     - 생성자를 통한 의존성 주입 : <constructor-arg> 태그와 ref 속성 이용
     - 속성을 통한 의존성 주입 : <property> 태그를 사용, name 속성값이 호출하고자 하는 메소드의 이름
  2. Annotation을 통한 의존성 주입
     **@Autowired** 라는 어노테이션을 통해 의존성 주입. 비슷한 역할로 **@Resource** 어노테이션도 존재.
     둘의 차이점은 bean을 탐색하는 우선순위의 기준

---

### AOP

- AOP의 핵심은 **관심 분리(Separation of Concerns)** 로써, <u>비즈니스 메소드를 개발할 때, 핵심 비즈니스 로직과 공통 로직을 분리함으로써 응집도가 높게 개발할 수 있도록 지원하는 것</u> 입니다.

  ![aop](https://t1.daumcdn.net/cfile/tistory/185DF4334FA8A1FD01)

:heavy_check_mark: **Aspect Oriented Programming** : 관점 지향 프로그래밍

- 핵심적인 비즈니스 로직과 관련이 없으나 모듈성을 높일 목적으로 여러 곳에서 공통적으로 쓰이는 기능들을 분리( separating cross-cutting concerns)하여 개발하고 실행 시에 서로 조합
- Logging, Security, Transaction 등을 aspect라는 특별한 객체로 모듈화, weaving이라는 작업을 통해 모듈화한 코드를 핵심 기능에 넣음

---

### PSA

:heavy_check_mark: **Potable Service Abstraction** : (이식 가능한)일관성 있는 서비스 추상화

- POJO로 개발된 코드는 특정 환경이나 구현 방식에 종속적이지 않아야 함
  (특정 환경에 종속적이지 않다는 게 그런 기술을 사용하지 않는다는 뜻은 아님)
- 스프링은 완성도가 높은 라이브러리와 연결할 수 있는 인터페이스를 제공

---

<br><br><br>
