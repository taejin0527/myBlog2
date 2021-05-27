---
title: C-CDA 란?
author:
  nick: TAEJIN
  link: null
categories:
  - 기타 📦
tags:
  - CDA
  - HL7
date: 2019-01-28 16:08:17
subtitle:
cover: "http://vico.org/CDAR22005_HL7SP/infrastructure/cda/graphics/L-POCD_RM000040.gif"
---

### Related Posts

---

> 본 문서는 IHIS 연구소의 **'HL7 C-CDA 교육'** pdf 문서를 기반으로 작성 되었습니다.

---

## Pre-Consolidation context

##### CDA 통합 이전

컴퓨터와 인터넷이 보편화 되고 사람들의 기대수명이 높아지면서 ICT(Information and Communication System) 기술을 보건의료 영역에 적용하려는 움직임이 시작 되었습니다.
하지만 병원과 기관마다 서로 다른 소프트웨어를 사용하기 때문에 정보 교환 또는 호환이 어려운 문제점이 있었습니다. 이를 해결하고자 _HITSP, HL7, IHE, Health Story_ 등의 여러 기업 및 기관들이 표준화된 **CDA(Clinical Document Architecture)**를 규정하고, 많은 사람들이 자신들의 표준을 사용하게 하기 위해 **CDA Implementation Guide(CDA IG)** 를 배포하였습니다.
각각의 표준은 비슷하지만 조금씩은 차이가 있었기 때문에 진정한 표준이 되지 못하고 다람쥐 쳇바퀴 돌 듯 이 문서들 간의 교환 및 교환의 문제가 발생하였습니다.

![C-CDA](/img/c-cda.png)

## Consolidated CDA

2012년 <u>the Office of the National Coordinator for Health Information Technology(ONC)</u> 에서 이러한 문제점을 해결하고자 **Consolidated CDA 라는 통일된 표준** 을 제시하였다고 위키피디아[^1]에 적혀있습니다. 저는 대중적으로 많이 사용하는 HL7 기관에서 2011년 12월에 발표한 'A draft Implementation Guide for CDA Release 2.0, Consolidated CDA Templates'[^2]를 기반으로 다룰 것 입니다.

**C-CDA IG** 는 아래와 같은 의료 문서를 포함합니다(year released)

- Consultation Note(2008)
- Discharge Summary(2009)
- Imaging Integration and DICOM Diagnostic Imaging Reports(DIR)(2009)
- History and Physical(H&P)(2008)
- Operative Note(2009)
- Progress Note(2010)
- Procedure Note(2010)
- Unstructured documents(2010)

![C-CDA2](/img/c-cda2.png)

## C-CDA IG Navigation

Consolidated CDA 작성 방법에 대한 자세한 정보는 공식 홈페이지를 참조하면 될 것 같습니다.
[HL7 Implementation Guide for CDA Release 2:IHE Health Story Consolidation, Release 1.1 - US Realm](http://www.hl7.org/implement/standards/product_matrix.cfm)

<br><br><br>

[^1]: [Consolidated Clinical Document Architecture 탭에 있음](https://en.wikipedia.org/wiki/Clinical_Document_Architecture)
[^2]: 초안의 사본은 HL7 웹 사이트를 가면 쉽게 찾을 수 있습니다.
