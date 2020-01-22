---
layout:     post
title:      "About OneR"
subtitle:   "One Rule 구하기"
date:       2019-09-11 18:32:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Data_Mining
tags:
  - Data mining
---

## Inferring rudimentary rules

- 높은 정확도

- single attribute 를 test 해봐야 한다.

- 각 attribure들에 대해서 속성들의 value들을 다 검사해줘야 한다.

weather domain(nominal)을 예를 들어 보자.

![WD](/img/in-post/Data_mining/weatherdomain.PNG)</br>

- outlook = sunny

outlook = sunny일 때 recommendation 은

yes = 2

no = 3 이다.

여기서 다수의 recommendation으로 결정한다. (같을때는 무엇을 택해도 같다.)

if outlook = sunny, then play = no

erros = 2/5

value들을 다 검사해줘야 하기 때문에, 3개의 value(sunny, overcast, rainy)를 다 검사해보자.

- outlook = overcast

yes = 4

no = 0

if outlook = overcast then play = yes

eroos = 0/4

- outlook rainy

yes = 3

no = 2

if outlook = rainy, then play = yes

erros = 2/5

outlook의 총 error rate = 4/14

각 attribute 중에 가장 에러가 작은 것을 골라야 한다.

> Temperature, Humidity, Windy 를 고려해야 한다는 뜻이다. 각자 계산해보자 ㅎ

weather domain(numeric)

![WDN](/img/in-post/Data_mining/weatherdomain(numeric).PNG)</br>

numeric은 continuous 하기 때문에 어느 특정값에 대해 정하기 어렵다.

sort를 하자.

ex) 14개의 instance에서 3개의 class가 생기면 다수로 하자!

- hummidity

85, 90, 86, 96, 80, 70, 65, 95, 70, 80, 70, 90, 75, 91
n   n   y   y   y   n   y   n   y   y   y   y   y   n

sort -> 65, 70, 70, 70, 75, 80, 80, 85, 86, 90, 90, 91, 95, 96
        y   y   y   n   y   y   y   n   y   y   n   n   n   y
        
(같은 70의 값이라면, 어느 값을 넣어도 상관없다.)

65, 70, 70, 70 (3개의 y 1개의 n)
y   y   y   n

하지만 인접한 수치를 봤을 때, 같은 class라면 구간을 넓힐 수 있다.

65, 70, 70, 70 (3개의 y 1개의 n)
y   y   y   n

-> 65, 70, 70, 70, 75, 80, 80
   y   y   y   n   y   y   y
   
구간을 정했다!

80과 85의 중간값 82.5
 
if 65<= hummidity < 82.5, then play = yes

erros = 1/7

이 과정을 끝날때까지 반복.

break point = 같은 값을 가지다가 달라지면

반복 하면, 마지막에 총 error rate = 3/14

여기까지 offline one rule

가장 error rate 가 작은 hummidity가 offline one rule
