---
layout:     post
title:      "SystemSecurity"
subtitle:   "보안의 기초 개념"
date:       2019-08-30 21:31:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: System_Security
tags:
  - System_Security
---

## SystemSecurity

### Characters

Alice, Bob = Good guys

Trudy = Bad guys

> Trudy는 "intruder"에서 기원

Alice's Online Bank (AOB)

Bob = Bank User

Trudy = Attacker

### Security Concern

개발자의 입장, 사용자의 입장, 공격자 입장이 다 다르다.

## CIA

#### Confidentiality = 비밀성 (보안에서는 Read에 대한 비밀성)

허가되지 않은, 권한이 없는 사람이 정보를 읽을려고 하는것을 방지해야 한다.

#### Integrity = 무결성 (보안에서는 Write에 대한 무결성)

Trudy가 Bob의 통장 잔고를 절대로 바꾸게 해서는 안된다.

이는 Bob도 마찬가지다.

Bob 또한 자신의 통장 잔고를 맘대로 바꾸게 해서는 안된다.

#### Availability = 유효성 (보안에서는 접근에 대한 유효성)

Bob은 AOB의 정보가 필요할때, 언제든 정보를 받을 수 있어야 한다.



Case 1 : Bob이 그의 컴퓨터에서 로그인을 할려고 한다.

Bob의 컴퓨터는 그가 "Trudy"인지, 진짜 "Bob"인지 어떻게 구분할 것인가?

이때 필요한 것이 검증된 Password이다.

이때, Password는 똑똑한 암호화 방식을 필요로 한다.

> 즉, 다른 사람이 이 암호를 알아내지 못하게 만들어야 한다.

Access Control (접근 제어)

1. Authentication = 인증

2. Authorization = 권한 (1급 기밀, 2급 기밀... etc)

"Butterfly Effect"

지구 반대편의 나비의 날개짓 한번이, 태풍으로 온다.

***암호화***

- 조금만 바꿔도 완전 견고해질 수 있다.

- 조금만 바꿔도 문제가 생길 수 있다.
