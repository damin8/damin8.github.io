---
layout:     post
title:      "Strategy Pattern"
subtitle:   "About Strategy Pattern"
date:       2019-10-02 21:43:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Design_Pattern
tags:
  - Design_Pattern
---

### Strategy Pattern

- 전략을 쉽게 바꿀 수 있도록 해주는 디자인 패턴!

- 여기에서의 전략 -> 목적을 달성하기 위해 일을 수행하는 방식, 비지니스 규칙, 문제를 해결하는 알고리즘

- 프로그램에서 쉽게 전략을 바꿔야 할 필요가 있는 경우 빈번하게 발생

![그림5-2](/img/in-post/Software/그림5-2.PNG)<br>

이런 경우를 보자.

이런 경우, 새로운 로봇을 추가하기는 쉽다.

> 새로 상속받은 클래스를 만들어주면 끝!

하지만, 태권 브이의 움직임이 변한다면? (걷기 -> 날기)

아톰의 공격이 변한다면? (펀치 -> 미사일)

태권 브이와 아톰에 있는 메서드(move or attack)를 바꿔줘야 한다!

> OCP 위반

이를 방지하고자 공격과 움직임을 (변하는 것) interface로 만들어 준다!

각각의 interface의 implements로 새로운 전략(Missile or Flying)을 클래스로 캡슐화!

![그림5-4](/img/in-post/Software/그림5-4.PNG)<br>

이런식으로 만들어 준다!!

개선된 인터페이스!

![그림5-5](/img/in-post/Software/그림5-5.PNG)<br>


## 싱글턴 패턴

- 두 개 이상의 인스턴스가 생성되는 것을 막는다

- 인스턴스가 사용될 때에는 동일 인스턴스를 사용하게 하는 것

### 한 부서에서 하나의 프린터만 사용하자!

~~~
public class Printer{
  public Printer(){
  
  }
  public void print(Resource r){
  }
}
~~~

이렇게 되면!

여기저기에서 new 생성자로 여러 개를 생성 할 수 있다!

> 왜? 생성자가 public이기 때문에

우선 1단계!

~~~
public class Printer{
  private Printer(){ }
  public void print(Resource r){
  }
}
~~~

private으로 생성자를 만들어서 class에서 접근을 못하도록 막아준다!

이렇게 되면 객체 생성은 누가..? 라는 문제가 생긴다

~~~
public class Printer{
  private static Printer printer = null;
  private Printer(){ }
  
  public static Printer getPrinter(){
    if(printer == null)
      printer = new Printer();
      
    return printer;
  }
  public void print(Resource r){
  
  }
}
~~~

자체적으로 printer 객체를 만들어 준다

getPrinter를 통해 printer를 return 받는다

객체를 만들 수 없기 때문에 getPrinter 메서드를 static으로 만들어서 객체가 없을 때 활용한다!

예를 들어보자

~~~
class Printer{
  private static Printer printer = null;
  public name;
  public age;
}
~~~

이런 Printer 클래스가 있다면

10개의 객체를 만들게 된다면

name, id 는 10개의 각각의 값을 가지게 된다.

하지만 static으로 선언된 printer는 단 1개만 만들어져서

10개의 객체가 참조하게 되는 것이다.

