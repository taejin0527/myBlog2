---
title: 스프링 프레임워크 모듈
author:
  nick: TAEJIN
  link: null
categories:
  - WEB 🌏
  - SPRING
tags:
  - FRAMEWORK
  - MODULES
date: 2019-01-31 19:08:32
subtitle: 스프링 프레임워크의 약 20개의 모듈들
cover: https://spring.io/img/spring-by-pivotal.png
---

---

## 스프링 프레임워크 모듈

![framework modules](https://docs.spring.io/spring/docs/4.3.22.RELEASE/spring-framework-reference/htmlsingle/images/spring-overview.png)

위 그림에 나와있듯이 스프링 프레임워크는 약 20개의 모듈들로 이루어져 있습니다.

- Data Access/Integration; Web; AOP; Aspects; Instrumentation; Messaging; Core Container; and Test;

|       모듈 그룹        |                                                       설명                                                        |
| :--------------------: | :---------------------------------------------------------------------------------------------------------------: |
|     Core Container     |                                      \* 스프링 프레임워크의 기본 모듈을 포함                                      |
| AOP 및 Instrumentation |     \* 관점 지향 프로그래밍(AOP; Aspect-Oriented Programming) 및 Class Instrumentation을 지원하는 모듈을 포함     |
|       Messaging        | \* 프로그래밍 모듈을 기반으로한 스프링 MVC 어노테이션 처럼 메세지를 메소드에 맵핑 시키는 어노테이션의 세트를 포함 |
| Data Access/Inegration |                           \* DB 및 메시징 공급자와의 상호작용을 간소화하는 모듈을 포함                            |
|          Web           |                            \* 웹 및 포틀릿 애플리케이션 개발을 간소화하는 모듈을 포함                             |
|          Test          |                             \* 단위 및 통합 테스트 생성을 간소화하는 모듈 하나를 포함                             |

이처럼 스프링은 **웹 애플리케이션 개발, 데이터베이스 접근, 트랜잭션 관리, 단위 및 통합 테스트 생성** 등등 엔터프라이즈 애플리케이션 개발의 모든 측면을 지원하고 이렇게 다양한 기능 중 우리는 필요한 것만 선택적으로 사용하면 됩니다.

만약 개발하고 있는 애플리케이션에서 스프링의 DI 기능[^1]을 사용하려면 Core Container 모듈 그룹에 속한 Spring-Core나 Spring-Beans 모듈을 선택해 사용하면 됩니다.

### 스프링 프레임워크 모듈 간 상호의존성

![dependency](https://1.bp.blogspot.com/-8MEJX0VwvO8/Wi0I3qLwk7I/AAAAAAAAgo0/nu7QGP77ZjA8hgCHdwDmjdgKNMJYjf_EACLcBGAs/s1600/1.1.png)

- **Core Container** 그룹이 스프링 프레임워크의 중심
- **AOP 및 Instrumentation** 그룹에 포함된 모듈도 이를 의존하는 다른 모듈이 많기에 중요도가 높음

지금은 이해가 잘 안되지만 앞으로 각각의 모듈들에 대해 자세히 알아볼 예정입니다.

다음 포스팅에서는 각각의 모듈들을 알아가기 전에 꼭 알아둬야하는 개념들을 가볍게 집고 넘어가겠습니다.

- 제어의 역적(IoC); 의존성 주입(DI); 관전 지향 프로그래밍(AOP); Model View Control(MVC);

![modules todo](https://d2h0cx97tjks2p.cloudfront.net/blogs/wp-content/uploads/sites/2/2018/06/Spring-Framework-Modules-01.jpg)

<br><br><br>

[^1]: DI 기능에 대해서는 다음에 따로 포스트할 예정(포스팅 하면 수정!!)
