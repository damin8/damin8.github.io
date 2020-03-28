---
layout:     post
title:      "Spring IoC,DI"
subtitle:   "About Ioc,DI,AOP"
date:       2020-03-27 22:31:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Spring
tags:
  - Spring
---

## 환경

- Spring Boot 2.2.5

## IoC

**Inversion of Control** = 제어의 역전

이것을 말하기 전에 라이브러리와 프레임워크의 차이점이 중요하다.

코드를 작성한다고 생각해보자.

우리는 특정 상황에 어떤 기능이 필요해 라이브러리를 사용하여 기능을 수행하는 경우가 있다.

이때는 우리가 주체가 되어 코드를 작성하는 것이다.

하지만 프레임워크는?

뼈대라고 생각하면 편하다. 우리는 그 뼈대에 맞춰 개발을 하고, 그에 맞게 조립하는 것이다.

프레임워크는 자신이 흐름을 제어하는 주체(ex. Spring Container)가 되어, 필요 할 때마다 코드를 호출하여 사용한다.

Spring Container는 객체의 생성, 소멸 등등 Life Cycle을 직접 관리한다.

따라서 객체의 제어권은 사용자에게 있는 것이 아니라, Spring Container 에게 있는 것이다.

이것을 **Inversion of Control** (IoC) 라고 부른다.

## DI

대부분의 Framework에서 IoC를 적용한다.

하지만 Spring Framework가 다른 Framework와 차별된 기능은 DI 이다.

**Dependency Injection** = 의존성 주입

의존적인 객체를 직접 생성 or 제어를 하는 것이 아니다.

특정 객체가 필요하다면 객체를 외부(ex. Spring Container)에서 가져다가 주입하는 것이다.

이렇게 된다면 객체를 외부에서 가져다가 쓰기 때문에 **new 연산자**가 사라진다.

클래스에서 **new 연산자** 대신에 외부에서 가져다가 주입하기 때문이다.

Spring Container에서 각 객체를 생성할 때는 단 1번만 실행이 된다.

이 뜻은 바꿔 말하면 Singleton이라고 말할 수 있다.

따라서 일반적인 Java에서 private static 등등의 수고를 하지 않더라도 자동적으로 만들어 준다.

## AOP

**Aspect-Oriented Programming** : 관심 지향 프로그래밍

여러가지 모듈에 공통적으로 쓰이는 기능이 있을 것이다.

쉬운 예를 들어보자.

나는 개인적으로 개발을 할 때 log를 남기는 것을 좋아한다.

따라서 어느 메서드던 간에 log를 만들어 에러가 났을 때 log를 보고 대처한다.

하지만 메서드가 10개, 20개 ... 등으로 늘어난다면?

까먹거나, 귀찮거나 할 수 있다.

만약 이 log를 관리할 수 있다면?

AOP를 이용해 모든 메서드에 log를 **언제, 어디서, 어떻게** 등등.. 추가 할 수 있다.

따라서 AOP가 모든 메서드에 log를 하나하나 코드를 작성하는 수고를 덜어준 것이다.

쉬운 예를 들어 설명했지만 실제로 공부해보면 여러가지 어려운 단어들이 나온다.

나도 공부를 더 해야겠다.

<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>


