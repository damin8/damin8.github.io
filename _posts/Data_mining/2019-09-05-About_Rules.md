﻿---
layout:     post
title:      "About Rules"
subtitle:   "다양한 Rule의 개념"
date:       2019-09-05 17:16:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Data_Mining
tags:
  - Data_mining
---

## divide-and-conquer

### nominal

divide = 나누기

> ex) weather domain에서 outlook -> sunny, overcase, rainy

conquer 정복할때까지 나누기.

> 규칙이 나올때 까지

### numeric

이분 탐색으로 나누기

## Classification rules

### if ~~~ then ~~~

antecedent = 앞 부분

consequent = 뒷 부분 (Class)

전체의 조건이 다 true = Firing

## Association rules

class 구분 없이 모든 attribute

Coverage = Instance의 빈도?

> 14개의 Instance중에 IF temperature = cool THEN humidity = normal 인 것은 4개 = 4 days(4/14)

Accuracy 

> temperature = cool을 가진 4개의 Instance 중에 humidity = normal인 것이 4개 = 100%(4/4)

## Rules with exceptions

새로운 데이터에 맞는 recommendation이 없을 수도 있다.

이럴때를 대비해서 예외를 둔다.

예외를 두면, 새로운 데이터가 다 예외라면 계속 예외를 둘건지?

-> 단점

## Instance-based Learning

rule을 찾는것 대신에, Instance 자체에 대해 집중한다.

Distance metric

-> 각각의 새로운 instance는 존재하는 instance와 비교하여 거리를 계산한다.

-> 가장 가까운 instance 클라스로 배정

> 스케일이 다르면 공평하지 않기 때문에 각각의 numeric 값을 정규화 시켜야 된다. (1~100, 1~10000)

Instance-based의 단점

- knowledge가 명확하지 않다.

- instance가 100만개라면 다 비교해줘야 하기 때문에 복잡도가 늘어난다.
