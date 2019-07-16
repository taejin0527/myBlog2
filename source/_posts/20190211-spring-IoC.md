---
title: 스프링 - IoC Containers
author:
  nick: TAEJIN
  link: null
categories:
  - WEB
  - SPRING
tags:
  - null
date: 2019-02-11 16:15:05
subtitle: 스프링 IoC 컨테이너에 대해 알아보자
cover: https://spring.io/img/spring-by-pivotal.png

---

### Reference

- [Spring IoC Containers – Types of Spring Container](https://data-flair.training/blogs/spring-ioc-containers/)
- [Spring 공식 문서](https://docs.spring.io/spring/docs/5.1.4.RELEASE/spring-framework-reference/core.html#spring-core)
- [Spring - IoC & DI](https://isstory83.tistory.com/91)

------


` 아직 많은 것을 알지 못하기 때문에 자세하고 정확한 내용은 제가 참조한 사이트나 따로 검색 또는 책을 통해 알아보는 것을 권장드립니다.`



## 용어정리

<span style="color:green">Bean</span> - **빌더 형식의 개발도구에서 가시적으로 조작이 가능하고 또한 재사용이 가능한 소프트웨어 컴포넌트**
: 썬 마이크로시스템즈에서 정의한 자바빈. 명칭의 유래는 자바(java)를 개발할 때 개발자들이 커피를 너무 많이 소비하여 커피가 그들의 상징으로 사용하였고, 커피콩(beans)은 작은 커피콩처럼 코딩의 작은 부분들을 나타냅니다.



<span style="color:green">Spring Bean</span> - **스프링 IoC 컨테이너로 DI(의존성 주입)을 통해 구성 요소를 관리하는 객체**
: 자바빈, EJB의 빈과 비슷한 오브젝트 단위의 애플리케이션 컴포넌트를 말합니다. 하지만 스프링을 사용하는 애플리케이션에서 만들어지는 모든 오브젝트가 빈은 아닙니다. **스프링의 빈은 컨테이너가 생성과 관계 설정, 사용 등을 제어해주는 오브젝트를 가리킵니다.**



<span style="color:green">Container(IoC container)</span> - **개발자가 작성한 코드의 처리과정을 위임받은 독립적인 존재**
: 적절한 설정만 되어 있다면 누구의 도움 없이도 개발자가 작성한 코드를 스스로 참조한 뒤 알아서 객체의 생성과 소멸을 컨트롤 해줍니다. 스프링에서는 IoC 방식으로 bean을 관리한다는 의미에서 bean factory나 application context를 가리킵니다.



## IoC(Inversion of Control - 제어의 역전)

Inversion of Control(**IoC**)은 Dependency Injection(**DI**)라고 알려져 있기도 합니다. 엄밀하게는 DI는 아래의 그림과 같이 IoC 패턴 중 하나이지만 IoC의 개념을 잡는데 흔히 마틴 파울러의 *'Dependency Injection Pattern'* 글( [번역](http://wiki.javajigi.net/pages/viewpage.action?pageId=68) )을 참고하다 보니 그런 것 같습니다.

![ioc](https://img1.daumcdn.net/thumb/R720x0.q80/?scode=mtistory&fname=http%3A%2F%2Fcfile10.uf.tistory.com%2Fimage%2F252FCF3B5231689B17B553)

 <span style="color:red;">DL (Dependency Lookup) - 의존성 검색</span>

- 저장소에 저장되어 있는 빈(Bean)에 접근하기 위하여 개발자들이 컨테이너에서 제공하는 API를 이용하여 사용하고자 하는 빈을 검색(Lookup)하는 것

 <span style="color:red;">DI (Dependency Injection) - 의존성 주입</span>

- 각 계층 사이, 각 클래스 사이에 필요로 하는 의존 관계를 컨테이너가 자동으로 연결해 주는 것
- 각 클래스 사이의 의존 관계를 빈 설정(Bean Definition) 정보를 바탕으로 컨테이너가 자동으로 연결해 주는 것
- **DL 사용시 컨테이너 종속성이 증가하여, 이를 줄이기 위해 DI를 사용**

<span style="color:blue;">Setter Injection</span>

- 객체를 생성 후 의존성 삽입 방식이기에 구현시에 좀 더 유연하게 사용
- setter()를 통하여 필요한 값이 할당되기 전까지 객체를 사용할 수 없음
- 스프링 프레임워크의 빈 설정 파일에서 property를 사용

```xml
<bean id="exampleBean" class="examples.ExampleBean">
	<property name="beanOne"><ref bean="anotherExampleBean"/></property>
    <!--setter injection using the neater 'ref' attribute -->
    <property name="beanTwo" ref="yetAnotherBean"/>
    <property name="integerProperty" value="1"/>
</bean>

<bean id="anotherExampleBean" class="examples.AnotherBean"/>
<bean id="yetAnotherBean" class="examples.YetAnotherBean"/>
```

```java
public class ExampleBean
{
    private AnotherBean beanOne;
    private YetAnotherBean beanTwo;
    private int i;

    public void setBeanOne(AnotherBean beanOne)
        this.beanOne=beanOne;

    public void setBeanTwo(YetAnotherBean beanTwo)
        this.beanTwo=beanTwo;

    public void setIntegerProperty(int i)
        this.i=i;
}
```





<span style="color:blue;">Constructor Injection</span>

- 생성자에 파라미터를 지정함으로 생성하고자하는 객체가 필요로 하는 것을 명확하게 알 수 있음
- 생성의 순서를 지켜야 하기 때문에 불편
- 스프링 프레임워크의 빈 설정 파일에서 constructor-arg 사용

```xml
<bean id="exampleBean" class="examples.ExampleBean">
	<constructor-arg><ref bean="anotherExampleBean"/></constructor-arg>
    <constructor-arg ref="yetAnotherBean"/>	<!-- 위 아래 동일한 방법 -->
    <constructor-arg type="int" value="1"/>
</bean>

<bean id="anotherExampleBean" class="examples.AnotherBean"/>
<bean id="yetAnotherBean" class="examples.YetAnotherBean"/>
```

```java
public class ExampleBean
{
    private AnotherBean beanOne;
    private YetAnotherBean beanTwo;
    private int i;

    public ExampleBean(AnotherBean anotherBean, YetAnotherBean yetAnotherBean, int i)
    {
        this.beanOne=anotherBean;
        this.beanTwo=yetAnotherBean;
        this.i=i;
    }
}
```



<span style="color:blue;">Method Injection</span>

- Singleton 인스턴스와 Non-Singleton 인스턴스의 의존 관계를 연결 시킬 필요가 있을 경우 사용하지만, 많이 사용되지는 않습니다.





## Spring IoC Container

<img src="http://www.javachain.com/wp-content/uploads/2014/07/Beanfactory1.png">

스프링 프레임워크의 IoC 컨테이너에는 크게

- **Bean Factory** (org.springframework.beans)
- **Application Context** (org.springframework.context)

두 종류가 있습니다.



#### 1. Bean Factory



<br><br><br>
