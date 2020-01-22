---
layout:     post
title:      "State Pattern"
subtitle:   "About State Pattern"
date:       2019-10-25 21:43:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Design_Pattern
tags:
  - Design Pattern
---

# State Pattern

- 실세계의 많은 시스템 = 다양한 상태 존재

- 동일한 자극에 대해 상태에 따라 다른 행위

~~~
친구가 장난칠 때

-> 우울한 상태

-> 행복한 상태

같은 장난 다른 반응
~~~

### 상태 머신 다이어그램

상태 머신 다이어그램 : 상태와 상태 변화를 모델링하는 UML 도구

- 상태 : 객체가 가질 수 있는 어떤 조건이나 상황

-> 전구 on/off

- 상태 전이/진입 : 객체의 한 상태에서 다른 상태로의 이동

-> 특정 이벤트 발생한 후 명세된 조건 만족 -> 전이

-> 이벤트[조건] / 액션

-> switch_on[power exists] / turnOn()

![그림7-1](/img/in-post/Software/그림7-1.PNG)<br>

~~~
초기 상태 = OFF

OFF 상태에서 스위치를 키면 switch_on 이벤트 발생

-> 만약 power_exists가 만족하면 ON 상태로 진입 -> turnon 액션 실행

-> 만족하지 못하면 OFF 상태에 머무른다

ON 상태에서 동작 버튼 누르면 run 이벤트 발생

-> WORKING 상태로 진입 -> operate 액션 실행!

ON or WORKING 상태에서 스위치를 끄면 switch_off 이벤트 발생

-> OFF 상태로 진입

~~~

![그림7-2](/img/in-post/Software/그림7-2.PNG)<br>

간략화 한 사진

OFF 상태에서 switch_on 이벤트 발생 -> Active 복합 상태로 진입

-> 묵시적으로 ON 상태로 진입

![그림7-3](/img/in-post/Software/그림7-3.PNG)<br>

이에 대한 코드

~~~
public class Light{
  private static int ON = 0;
  private static int OFF = 1;
  private int state;
  
  public Light(){
    state = OFF;
  }
  
  public void on_button_pushed(){
    if (state == ON){
      System.out.println("반응 없음");
    }
    
    else{
      System.out.println("Light On!");
      state = ON;
      
    }
  }
   public void off_button_pushed(){
    if (state == OFF){
      System.out.println("반응 없음");
    }
    
    else{
      System.out.println("Light Off!");
      state = OFF;
      
    }
  }
}
~~~

만약 여기에 "Sleeping" 모드가 추가 된다면?

ON 에서 Sleeping 모드로 가는 방향이 생기고

Sleep에서 ON 모드로 가는 것도 생긴다.

-> 유지 보수 너무 안좋다!!

-> OCP 원칙 위반!!!!!

-> 변하는 '상태' 를 기준으로 


### Strategt pattern 과 State pattern 의 차이!

State = State 변화를 State가 가지고 있다.

-> 이벤트만 주어서 State 안에서 변화를 한다.

-> State가 상태를 바꿔줄 수 있다. (setState는 ON, OFF가 사용!)

-> Client는 전혀 사용 x

Strategy = Client에서 set을 이용해 바꿔 주어야 한다.

-> 그 전의 Strategy 에서 Robot은 Client가 사용한다.

둘이 비슷해 보여도 이런 차이점을 가지고 있다.

혼동 말기를!!
