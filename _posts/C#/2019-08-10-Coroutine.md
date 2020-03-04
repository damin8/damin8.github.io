---
layout:     post
title:      "Coroutine"
subtitle:   "About Coroutine"
date:       2019-08-10 21:31:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: C_sharp
tags:
  - C_sharp
---

## Coroutine 에 대하여

Unity를 공부하던 중에, Coroutine이라는 개념이 중요하다고 해서 공부를 했습니다.

우선 설명이 잘 되어 있고, 제가 공부했던 사이트는 [Coroutine](https://kwangyulseo.com/2015/05/15/%EC%BD%94%EB%A3%A8%ED%8B%B4coroutine-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0/)입니다.

게임 프로그래밍은 수많은 게임 object들의 상호 작용으로 표현 됩니다.
(ex. 비행기 움직이기, 그 비행기에서 미사일 쏘기 등등..)

이것들이 부자연스럽게 움직이게 되면 굉장히 어색하게 보일겁니다.
따라서 게임 프로그래밍에서는 동시성(concurrency)을 표현하는 것이 중요합니다.

Unity는 .Net을 사용하지만, Multi thread가 아닌, Coroutine으로 동시성을 표현합니다.

> 왜? -> Multi thread로는 버그 없는 코드를 작성하기가 어렵다고 합니다.

### Coroutine 용어 정의

Coroutine은 Subroutine을 2개의 축으로 확장한 강력한 Subroutine입니다.

1. 여러 개의 입구를 허용하여 실행 재개가 가능

2. 멈춤 시 돌아갈 위치 지정

일반적인 Subroutine은 호출될 때마다 메소드의 처음부터 실행을 시작

return -> 항상 호출자로 돌아감.

Coroutine은 이전 상태를 기억하고 있어서 호출 시 이전 호출에서 멈춘 위치에서부터
다시 실행 재개, 멈출때는 자신이 지정한 위치로 돌아감.

> 일반적인 Subroutine <br>
- 한국인 나그네가 미국을 갔다가, 다시 한국으로 돌아옴.<br>
Coroutine <br>
- 한국인 나그네가 미국을 갔다가, 미국에 있거나, 다른 곳으로 여행.(자유롭다)

이 차이만 보더라도, Coroutine은 정말 중요한 개념인것 같습니다.

Unity 프로그래밍에서 Coroutine이 중요한 이유 -> 협력형 멀티태스킹

### 협력형 멀티태스킹이란?

일종의 시분할 방식으로 여러 task가 하나의 CPU를 나눠쓰는 방식

선점형 멀티태스킹과 달리 운영체제의 개입 없이 각 task가 독점적으로 CPU를 사용하고,

사용이 끝나면 자발적으로 양보 -> 강제로 CPU를 뺏기는 일이 없음.

- 임계구역(critical section)을 보하기 위한 락(Lock) or 세마포어(Semaphore)등 동기화 수단 필요 x

> 혹시 용어들을 모르신다면 운영체제에 대해 공부를 해주시길 바랍니다!

이상으로 Corutine에 대해 알아보았습니다!
언제나 feedback은 환영입니다!
읽어주셔서 감사합니다 ㅎ

