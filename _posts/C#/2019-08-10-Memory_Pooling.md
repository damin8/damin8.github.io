---
layout:     post
title:      "Memory Pooling"
subtitle:   "C# Memory Pooling"
date:       2019-08-30 21:31:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: C#
tags:
  - C#
---

## Memory Pooling

제가 사용하는 언어는 C#입니다.

C#에는 C++랑은 다르게, GC(가비지 컬렉터)라는 것이 메모리를 자동으로 관리해줍니다!

장점 -> 프로그래머의 수고를 덜어준다.

단점 -> 예기치 않은 "GC 호출" 입니다

GC는 객체가 사라질때마다 호출이 되어 많은 부하를 일으킵니다.

만약, 비행기 게임에서 미사일을 1000개를 발사하고 1000개를 다 Destroy 해준다면?

1000개가 아니더라도 10^10개를 발사해주고 다 Destroy 해준다면?

Destroy 함수가 호출된 다음에 바로 GC가 호출이 되기 때문에

과부하 -> 예기치 않은 렉.

따라서 Memory Pooling을 이용하는 겁니다!

### Memory Pooling이란?

배열처럼 미리 메모리 공간을 사용할 만큼 할당하여 그 안에 사용할 객체들을 미리 넣어둡니다.

예를들어 미사일 10개를 할당받고, 하나하나를 다 Destroy 해주는게 아니라,

현재 쓰고있지 않은 미사일을 활성화 시켜주고, 쓰고 있지 않거나 이미 쓴 것들은 비활성화 시켜줍니다.

따라서 이렇게 하게 되면 Destroy 함수를 쓰지 않기 때문에 최대한으로 GC의 호출을 막을 수 있습니다.

정말 좋은 [메모리 풀 클래스](https://hyunity3d.tistory.com/195)가 여기 있으니 나중에 참고하시면 될 거 같습니다.

읽어주셔서 감사합니다!
