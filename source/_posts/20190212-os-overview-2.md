---
title: 운영체제 - Overview_2
author:
  nick: TAEJIN
  link: null
categories:
  - OS
tags:
  - OS
  - 운영체
date: 2019-02-12 18:51:53
subtitle: 컴퓨터 시스템 구조
cover: https://safebytes.com/wp-content/uploads/2016/10/OperatingSystem-min.jpg
---

# 컴퓨터 시스템 구조

## 2.1 컴퓨터 시스템의 동작

<img style="height:450px; align:center;" src="https://i.imgur.com/8JAIHTg.png">

- 컴퓨터는 <u>공유된 주기억장치에 접근을 제공하는 공통 버스에 의해 연결된 CPU와 여러 개의 장치 제어기(Device controller)로 구성</u>되어 있습니다.
  - 장치 제어기(Device Controller)
    각 장치(디스크, 오디오 장치, 비디오 디스플레이)를 관리
  - 장치 제어기와 CPU는 병행으로 수행되므로 이들은 주기억장치 접근에 대해 경쟁합니다. 주기억장치 제어기(Memory Controller)는 이들의 접근을 동기화해줍니다.
- 컴퓨터가 처음 구동되면 초기에 실행될 프로그램이 필요합니다. 이 프로그램을 **부트스트랩 프로그램(Bootstrap program)** 이라고 합니다. 이 프로그램은 보통 컴퓨터 하드웨어 내에 ROM(Read-Only-Memory)에 저장되어 있습니다.
  - 부트스트랩 프로그램(Bootstrap program)
    모든 하드웨어를 초기화하고 운영체제 커널을 주기억장치에 적재한 후에 커널을 실행

<br>

- 컴퓨터에서 사건(Event)의 발생은 **인트럽트(interrupt)** 신호, **트랩(trap)** 혹은 **예외(Exception)** 를 통해 운영체제에 통보됩니다. 사건이 발생되면 CPU는 현재 수행중인 작업을 멈추고, 운영체제 내에 있는 특정 코드를 실행합니다. 이 실행이 끝나면 다시 멈춘 작업을 재개합니다.

<img height="250px" src="http://pediaa.com/wp-content/uploads/2018/08/Difference-Between-Trap-and-Interrupt_Figure-1.png">

<span style="color:red">Interrupt</span>

- **Hardware Interrupt** : 하드웨어는 CPU에 특정 신호를 보내어 인트럽트의 발생을 알림
  -- 예) 키보드 입력, I/O interrupt, timer ticks
- 하드웨어가 시스템의 수행 흐름을 바꾸기 위해 발생하는 것
- 비동기식(Asynchronus Interrupt)



<span style="color:red">Trap</span>

- **Software Interrupt** : 시스템호출(System call)이라는 특정 연산을 실행하여 일부로 발생시키거나 오류 때문에 자발적으로 발생
  -- 오류의 예) 0 나누기, 부적합한 주기억장치 접근(page fault)
- 동기식(Synchronus Interrupt)



<span style="color:red">Exception</span>

- 프로세서에 의해 자동으로 처리
- **Faults** 와 **Aborts** 로 세분화 가능
  -- Faults : 복구 가능한 오류 (recoverable error)
  -- Aborts : 처리하기 어려운 오류 (an error that is difficult to handle)

<br>

## 2.2 I/O 구조

- 장치 제어기(Device controller)에 따라 하나 이상의 장치가 제이거에 연결될 수 있습니다
- 장치 제어기는 지역 버퍼와 몇 개의 특수 목적 레지스터를 유지합니다
- 장치 제어기는 연결된 주변장치와 지역 버퍼 간에 데이터 이동을 책임집니다. 이 버퍼의 크기는 주변장치에 따라 다릅니다.



### 2.2.1 I/O Interrupt

- 입출력의 두 가지 형태
  -- 동기식 입출력(Synchronous I/O) : 입출력이 시작되면 요청한 프로세서는 입출력이 완료될 때까지 기다림
  -- 비동기식 입출력(Asynchronous I/O) : 요청한 프로세서는 입출력이 완료될 때까지 기다리지 않고 계속 다른 작업을 수행
- 입출력의 완료를 기다리는 방법
  -- 특수한 명령어 사용
  -- 대기 루프 사용
- <u>만약 CPU가 입출력 완료를 항상 기다리면</u> 한번에 한 입출력만 가능
  하지만 시스템의 효율을 높이기 위해 입출력과 계산을 병행할 수 있어야함으로 이 방법은 비효율적
- 운영체제는 여러 개의 입출력 요청을 관리하기 위해 **장치 상태 테이블(device-status table)** 을 유지합니다. 각 장치마다 대기큐를 유지합니다.

<img height="350px" src="https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/images/Chapter13/13_09_DeviceStatusTable.jpg">



### 2.2.2 DMA 구조

- 속도가 느린 입출력 장치는 하나의 입력을 받은 후에 다음 입력까지 CPU는 다른 유용한 작업을 할 수 있습니다.
  반대로 속도가 빠른 입출력 장치는 인트럽트가 너무 빈번하게 발생하여 CPU가 다른 유용한 작업을 할 시간이 없습니다.
- 이것을 해결하기 위해 사용하는 기법이 **DMA(Direct Memory Access)** 입니다.
- DMA 방식에서 장치 제어기는 데이터 블록을 CPU의 관여없이 직접 주기억장치로 이동하며, 인터럽트는 바이트 단위가 아닌 블록 단위로 발생합니다.

<img style="align:center;" src="http://pds17.egloos.com/pds/200910/26/90/c0098890_4ae5a423a7cef.jpg">

<br>

## 2.3 저장 구조

<img src="https://i.imgur.com/ofvb8E7.png">

- 컴퓨터 프로그래밍이 실행되기 위해서는 **주기억장치(main memory / primary storage / internal memory)** 에 적재되어야 합니다
- 주기억장치는 보통 <u>동적 임의접근 메모리(dynamic Random-Access Memory, RAM)</u>라고 하는 반도체 메모리를 사용
- <u>CPU가 직접 접근할 수 있는 기억장치</u>는 주기억장치뿐입니다



- 주기억장치의 한 구성 단위를 **워드(word)** 라 하며, 각 워드는 독특한 주소를 가집니다



- <span style="color:red">주기억장치의 크기 / 주기억장치의 휘발성</span> 때문에 모든 프로그램과 데이터를 주기억장치에 영구적으로 저장할 수 없습니다
- 이 문제를 해결하기 위해 많은 양의 데이터를 영구 보관할 수 있는  **보조 기억장치(auxiliary memory / secondary storage / external memory)** 를 사용합니다



### 2.3.1 주기억장치

- **Memory-mapped I/O**
   주기억장치의 일부 주소가 입출력을 위해 예약되어 있으며, 이 주소에서 읽거나 쓰면 장치 레지스터로부터 데이터를 읽거나 쓰는 결과가 되는 것
- CPU가 I/O 포트를 통해 연결된 장치와 데이터를 교환하는 2가지 방식
  -- **Programmed I/O** : CPU가 계속 장치의 상태를 검사(polling)하는 방식
  -- **Interrupt** : 다음 데이터를 처리할 준비가 되면 장치 제어기는 인터럽트를 통해 그 사실을 CPU에 알리는 방식
- 주기억장치와 CPU의 속도 차이를 극복하기 위해 주기억장치와 CPU 사이에 **캐시(cache)** 라고 하는 고속 메모리 버퍼를 사용

<img src="https://teachcomputerscience.com/wp-content/uploads/2016/12/cache_animation.gif">



### 2.3.2 보조기억장치(자기 디스크)

<img style="height:150px; float:right;" src="https://www.applexsoft.com/glossary/harddisk.jpg">

- 자기 디스크는 **플래터(platter)** 라고 하는 여러 개의 원형 판으로 구성
  이 플래터는 다시 원형 모양의 **트랙(track)** 으로 구성
  트랙은 다시 여러 개의 **섹터(sector)** 로 나뉘어짐

<img style="height:200px; float:right;" src="http://mblogthumb1.phinf.naver.net/20141226_132/capemay_1419579186649T86jM_PNG/010edsector.png?type=w2">

- 단순하게 섹터를 여러 개를 하나로 묶은 것을 **클러스터(cluster)** 라 하고,
  같은 위치에 있는 트랙의 모음을 **실린더(cylinder)** 라고 합니다
  -- 클러스터는 <u>운영체제에서 사용하는 데이터 저장의 최소 단위</u>



- **디스크의 속도** = 컴퓨터로 데이터를 전송하는 비율인 전송률(transfer rate)
  			 +plus+
  			 임의접근 시간(random-access time)이라고 하는 위치결정 시간(positioning time)
  에 의해 결정됩니다

- 데이터의 교환은 특수한 제어기를 통해 이루어집니다
  컴퓨터 연결 끝에는 호스트 제어기
  디스크 자체 내에는 디스크 제어기 가 있습니다
- 디스크 제어기는 자체적으로 캐시를 가지고 있습니다
- 실제 데이터는 디스크 제어기에 의해 디스크에서 캐시로 옮겨지고, 호스트 제어기는 캐시에 있는 데이터를 주기억장치로 옮깁니다



## 2.4 저장장치의 계층구조

<img src="https://eunhyejung.github.io/assets/contents/content03.PNG">

- 계층구조에서 위에 위치할 수록 속도는 빠르지만 고가이며 휘발성의 성질을 가집니다
- 두 저장장치의 속도 차이는 중간에 빠른 캐시를 설치하여 극복할 수 있습니다
- 시스템을 구성할 때 저장장치의 계층구조를 균형있게 잘 구성하면 저렴한 가격에 높은 성능을 얻을 수 있습니다



### 2.4.1 캐싱

- CPU가 데이터를 필요하면 먼저 캐시에 그 데이터가 있는지 검사합니다
  만약 있으면 캐시에서 바로 사용하고 없으면 주기억장치에 있는 데이터를 사용하지만 이 데이터의 복사본을 캐시에 보관합니다. 이는 데이터를 곧 다시 사용할 확률이 높기 때문입니다
- **캐시의 크기는 제한** 되어 있으므로 이것을 잘 관리하여야 시스템의 성능을 높일 수 있습니다. 캐시의 크기와 교체 정책(replacement policy)을 잘 선택하면 원하는 데이터가 캐시에 있을 확률을 80%에서 99%까지 높일 수 있습니다
- 주기억장치는 CPU와 보조기억장치 사이에 있는 캐시로 사용될 수 있습니다



### 2.4.2 일관성

- 저장장치의 계층구조를 사용하면 같은 데이터가 여러 레벨에 존재할 수 있습니다
- 한번에 하나의 프로세스만 동작하면 아무 문제가 되지 않지만!
  여러 프로세스가 같은 데이터를 접근하고자 하면 모든 프로세스가 최신의 데이터를 얻을 수 있도록 해야 합니다
  <u>이 문제는 다중프로세서 시스템에서 더욱 심각합니다</u>
- 분산 환경에서는 여러 파일의 복사본이 여러 컴퓨터에 분산되어 있을 수 있습니다. 따라서 하나의 복사본에 대한 갱신이 이루어지면 다른 복사본도 갱신되도록 하여야 합니다





## Reference

[Difference between Trap and Interrupt](http://pediaa.com/difference-between-trap-and-interrupt/)

[DMA-CPU몰래 영차영차](http://recipes.egloos.com/5152867)



<br><br><br>
