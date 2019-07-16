---
title: 운영체제 - Overview_1
author:
  nick: TAEJIN
  link: null
categories:
  - OS
tags:
  - 운영체제
  - OS
date: 2019-02-05 19:29:30
subtitle: 운영체제 복습(소개)
cover: https://safebytes.com/wp-content/uploads/2016/10/OperatingSystem-min.jpg

---

------

# 1. 소개

## 1.1 운영체제

<img src="https://www.tutorialspoint.com/operating_system/images/conceptual_view.jpg">

<img style="float:right;" src="https://upload.wikimedia.org/wikipedia/ko/thumb/a/a3/Operating_system_placement_kor.png/200px-Operating_system_placement_kor.png">

- 운영체제(Operating System)란?

  -- 컴퓨터 하드웨어를 관리하는 프로그램
  -- 응용 프로그램의 토대를 제공해주는 프로그램
  -- **<span style="color:orange;">사용자</span>와 <span style="color:red;">하드웨어</span> 사이에 중간 매개체 역할** 을 해주는 프로그램

- 운영체제 범위에 대한 정의
  하드웨어의 종류와 용도가 다양해서 OS의 범위는 모호하게 정의됩니다​
  정의 1) 운영체제를 구입하였을 때 포함되어 있는 모든 것
  <u>정의 2) 항상 수행되고 있는 유일한 프로그램(보통 **Kernel** 이라고 한다)</u>
  **대체로 2번 째 정의를 사용함**



그림에서 처럼 운영체제는 컴퓨터의 사용자와 컴퓨터 하드웨어 사이에 있기 때문에 운영체제를 바라보는 관점도 두 가지로 분류할 수 있습니다.

### 1.1.1 <span style="color:orange;">사용자 관점</span>

- **컴퓨터의 용도** 에 따라 OS의 설계 방향이 결정 됩니다.

  -- 개인용 컴퓨터(Home PC user)
  -- 메인프레임, 미니컴퓨터(Mainframe, minicomputer)
  -- 워크스테이션(Workstation)
  -- 휴대용 컴퓨터(Mobile devices)

### 1.1.2 <span style="color:red;">시스템 관점</span>

- **자원 할당자(resource allocator)**
  컴퓨터 자원(CPU 시간, 메모리 공간, 파일 저장 공간, 입출력 장치)의 할당은 공정해야 하며 효율적으로 이루어져야 합니다.
- **제어 프로그램(control program)**
  사용자 프로그램의 실행을 감독하여 오류와 컴퓨터 오용을 방지하고 입출력 장치의 제어와 동작을 관리 합니다.



### 1.1.3 운영체제의 목표

- <span style="color:orange;">사용자</span>에게 편리성 제공
- <span style="color:red;">컴퓨터 시스템</span>의 효율적 운영

**사용자에게 컴퓨터에서 프로그램을 효율적이고 편리하게 실행할 수 있는 환경을 제공** 하는 것 입니다!!



## 1.2 메인프레임 시스템

### 1.2.1 일괄처리 시스템(1950)

**Batch processing system이란 처리속도를 향상 시키기 위해 유사한 요구를 필요로 하는 여러개의 작업을 함께 모아 단일 작업으로 일괄 처리하는 시스템입니다**

- 운영체제는 항상 **메모리** 에 상주하고, 주 임무는 **하나의 작업에서 다음 작업으로 제어를 자동적으로 옮기는 것**

- 작업을 실행하면 끝날 때까지 다른 작업을 못함

- <span style="color:red">기계적 입출력 장치가 전자적 장치의 속도보다 상대적으로 느려 CPU가 종종 쉬는 경우가 발생</span>



<span style="color:blue">직접 접근(direct access)이 가능한 디스크의 도입 : Job scheduling과 multi-programming이 가능하게 됨</span>

### 1.2.2 다중 프로그램 시스템(1960)

**Multi-program system 이란 여러 개의 프로그램을 동시에 메모리에 적재하여 하나의 프로그램이 대기 상태가 되면 그 동안 다른 프로그램을 실행하는 시스템입니다**

- 입출력과 프로그램의 실행을 병행으로 수행할 수 있어 CPU의 사용 효율(utilization)이 증가
- 다중 프로그래밍에서 운영체제는 사용자를 대신하여 의사결정을 수행해야 함
  -- **Job scheduling** : 디스크에 있는 작업 저장소(Job pool)에서 작업을 선택하여 메모리로 옮기는 것
  -- **CPU scheduling** : 실행 중인 작업이 대기 상태가 되었을 때 메모리에 있는 작업 중 하나를 선택하여 CPU에 할당하는 것
- <span style="color:red">여러 프로그램이 동시에 메모리에 상주하므로 메모리 관리가 복잡</span>
- Multi programming을 제공하는 일괄처리 시스템은 <span style="color:red">CPU의 사용 효율은 높였지만 사용자와 컴퓨터 간에 상호작용은 제공하지 못함</span>



### 1.2.3 시분할 시스템(1960)

**시분할(Time sharing) 또는 멀티태스킹(multi-tasking)은 다중 프로그래밍과 달리 정해진 시간이 되면 무조건 다음 순서의 작업을 실행하는 방식** 으로 교대하는 시간이 매우 짧아 프로그램이 실행되는 동안 사용자는 컴퓨터와 상호작용이 가능한 시스템입니다

- 사용자와 시스템 간에 직접 상호작용이 가능한 시스템을 **대화식 컴퓨터 시스템(inter-active computer system)** 이라 하고 이런 시스템은 응답시간(response time)이 짧아야 함
- 여러 사용자가 동시에 컴퓨터를 사용할 수 있음
- 메모리에 적재되어 실행 중인 프로그램을 **프로세스(process)** 라고 함
- 많은 사용자의 프로그램을 동시에 수행하기 위해서는 *주기억장치* 의 용량으로는 부족
  <span style="color:blue">디스크를 주기억장치의 보조 저장 장치로 활용으로 문제를 해결하며 가장 널리 사용되는 기법으로 가상 메모리(virtual memory)</span> 가 있습니다



## 1.3 실시간 처리 시스템

**Real time processing system 이란** 프로세서 작동이나 데이터 흐름에 엄격한 시간 제약이 있을 때 사용되는 방식으로 **데이터 처리 요구가 있는 즉시 수행하여 결과를 산출하는 시스템입니다**

- 보통 특수 목적용(우주선 운행, 레이더 추적기, 핵물리학 실험, 은행의 온라인 업무)
  주의) <u>실시간과 빠르다는 것은 다른 개념!!</u>
- 엄격한 실시간 시스템(hard real-time system) : 중요한 작업이 정해진 시간 내에 완료됨을 보장
- 완화된 실시간 시스템(soft real-time system) : 중요한 작업이 우선순위를 가지지만 엄격하게 정해진 시간 내에 완료됨을 보장하지는 않음



## 1.4 분산 처리 시스템

**Distributed processing system 이란** 다중처리 시스템과 마찬가지로 **여러 프로세서(컴퓨터)를 사용**하지만 밀결합 형태가 아닌 소결합(loosely coupled) 형태로 컴퓨터 버스나 클럭을 공유하지 않고, **네트워크를 통해 통신하여 하나의 작업을 처리하는 시스템입니다**

- 네트워크는 사용하는 프로토콜, 망의 크기, 전송 매체에 따라 분류
  Ex) 망의 크기 : LAN, MAN, WAN



### 1.4.1 클라이언트-서버 시스템

- 서버 시스템은 크게 두 가지로 분류
  - 계산 서버 시스템(compute-server system)
    : 클라이언트로 부터 요청을 받아 그것을 대신 수행해 준 다음에 클라이언트에게 결과를 되돌려 줌
  - 파일 서버 시스템(file-server system)
    : 클라이언트에게 파일 시스템 인터페이스를 제공, 클라이언트는 이 인터페이스를 통해 파일을 생성, 갱신, 삭제



## 1.5 다중처리 시스템

**Multi-processing system 이란 여러 개의 CPU와 하나의 주기억장치를 이용하여 여러 개의 프로그램을 동시에 처리하는 방식을 취하는 시스템입니다**

- 병렬 시스템(parallel system) 또는 밀결합 시스템(tightly coupled system) 이라고도 함
- **처리율(throughput)** : <u>N개의 프로세서를 사용한다고 처리율이 N배 증가하지는 않음 </u>
- **경제성** : 여러 개의 단일 프로세서 시스템을 사용하는 것 보다 저렴
- **신뢰성** : 하나의 CPU가 고장나더라도 다른 CPU를 이용하여 업무를 처리할 수 있음
  수행되는 하드웨어의 수에 비례하여 서비스를 계속 제공할 수 있는 능력(graceful degradation)



## 1.6 집단 시스템

**Clustered system 이란 병렬 시스템, 분산 시스템과 마찬가지로 다중 CPU를 사용하지만 여러 개의 시스템을 밀결합하여 사용한다는 측면에서 다른 시스템입니다**

- 집단화(clustering)의 목적은 높은 가용성
- 대칭형 방식 : 각 컴퓨터는 모두 응용 프로그램을 수행하는 동시에 다른 컴퓨터의 상태를 감시
- 비대칭형 방식: 하나의 컴퓨터는 대기상태로 있고 나머지는 활성화되어 응용 프로그램을 수행



## 1.7 컴퓨팅 환경

- 초창기 컴퓨팅 환경은 중앙집중 --> 유선통신 기술의 발달로 분산 컴퓨팅 환경 등장 --> 무선통신 기술의 발달로 이동컴퓨팅(mobile computing) 환경 등장

- 인터넷의 발달로 현재의 컴퓨팅 환경을 웹 기반 컴퓨팅이라고 함
- 실시간 운영체제를 각종 기계와 장치에 내장하여 사용하는 컴퓨팅 환경을 **임베디드 컴퓨팅(embedded computing)** 환경이라고 함



<div style="border:3px; border-style:dashed; border-color:grey; text-color:black">
  <b> * 정리 * </b><br>
  1세대 : 일괄처리 시스템 <br>
  2세대 : 다중프로그래밍, 다중 처리, 시분할, 실시간 처리 시스템<br>
  3세대 : 다중모드 <br>
  4세대 : 분산 처리 시스템
  <br>
</div>

<br><br><br>
