---
layout:     post
title:      "Design Pattern"
subtitle:   "디자인 패턴이란?"
date:       2019-09-25 21:43:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Design_Pattern
tags:
  - Design Pattern
  - Software Engineering
---

### 디자인 패턴

소프트웨어를 개발하면서 발견된 점

-> 똑같은 문제가 발견된다!

많은 사람들이 문제들을 해결했을 것이다.

- 바퀴를 다시 발명하지 마라

> 이미 있는 바퀴를 갖다 쓰면 되는거지, 굳이 왜 또 만드는가?

그 많은 해결들중에 효과적인 해결법 = 디자인패턴

- 소프트웨어를 설계할 때 특정 맥락에서 자주 발생하는 고질적인 문제들이 발생했을 때 재사용할 수 있는 훌륭한 해결책

#### 순차 다이어그램

객체의 3가지 표현

![그림4-7](/img/in-post/Software/그림4-7.PNG)<br>

세미콜론(:)을 기준으로

앞 : 객체 이름

뒤 : 클래스 이름

객체의 이름은 소문자로 시작!

#### Sequence diagram

![그림4-8](/img/in-post/Software/그림4-8.PNG)<br>

화살표는 일을 시키는 것
  m1(a,b)
x   ->    y = x가 y의 m1(a,b) 메서드 호출 

점선 : 생명선 (x 표시는 죽었다는 뜻)

생명선에 있는 네모 = 네모의 시작부터 네모가 끝날 때 까지 역할 수행

꺽새 안에는 대표적으로 2가지가 들어간다

create = 객체 만들기(new)

destroy = 죽이기(delete or null)

3[g] : m2() = g가 만족하면 m2를 호출해라!! (if문)

-> Guard condition

중요한 사실!! Sequence diagram이 나오면 코드가 어느정도 나온다!

이 Sequence diagram을 코드로 작성해보자!!

~~~
public class Y {
  public void m1(A a,B b){
    Z o = new Z();
    if(g)
      o.m2();
  }
}

public class Z{
  private W w;
  
  public void m2(){
    w = null
  }
}
~~~

이렇게 코드가 나온다!

![153쪽CP](/img/in-post/Software/153쪽CP.PNG)<br>

이번에는 순차 다이어그램에 해당하는 코드를 작성해보자!

~~~
class A1{
  public void doA1(){
    A2 a2 = new A2();
    a2.doA2(this);
  }
  public void doIt(A3 a3){
    a3.doIt();
    }
  }
}

class A2{
  public void doA2(A1 a1){
    A3 a3 = new A3();
    a1.doIt(a3);
    }
  }
}
~~~

이렇게 코드가 나오게 된다!

#### alt

alt = if

![alt](/img/in-post/Software/alt.PNG)<br>

alt 는 sequence diagram에서 if문을 표현하는 방법이다!

alt에서 점선을 기준으로 윗부분은 ok가 true일 때
 
                        밑부분은 ok가 false일 때
                        
#### Loop

Loop = for or while

![그림4-11](/img/in-post/Software/그림4-11.PNG)<br>

Ok가 true가 아닌 동안 반복해라! (-> password가 틀리면 계속 반복)


