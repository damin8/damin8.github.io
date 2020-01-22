---
layout:     post
title:      "Command Pattern"
subtitle:   "About Command Pattern"
date:       2019-11-01 21:43:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Design_Pattern
tags:
  - Design Pattern
---


# Command Pattern

- 기능을 캡슐화로 처리

1. T1 시간에는 알람 Start!

2. T2 시간에는 램프 On!

Flexible 한 버튼을 만들고 싶다!!

이럴 때 Command Pattern 사용!

버튼을 눌러 램프를 켜보자!

![그림8-1](/img/in-post/Software/그림8-1.PNG)<br>

지금 보면 정말 Tight 하게 연결 되어 있습니다.

OOP에서는 Tight하게 연결 되어 있으면 안되죠?

일단 코드로 짜보겠습니다.

~~~
public class Lamp{
  public void turnOn(){
      System.out.println("LampOn");
    }
}

public class Button {
  private Lamp theLamp;
  public Button(Lamp theLamp){
    this.theLamp = theLamp;
  }
  public void pressed(){
    theLamp.turnOn();
  }
}
~~~

이렇게 코드가 나오게 되는데요

만약 버튼이 램프만을 위한 것이면 상관이 없습니다!

하지만 버튼은 다른 용도로도 사용할 수 있죠?!

Ex) 처음 눌렀을 때는 램프 키고, 두 번째 눌렀을 때는 알람 동작!

일단 버튼을 눌렀을 때 알람 시작하게 하는 코드를 짜보면

~~~
public class Alarm{
  public void turnOn(){
      System.out.println("Alarm!");
    }
}

public class Button {
  private Alarm theAlarm;
  public Button(Alarm theAlarm){
    this.theAlarm = theAlarm;
  }
  public void pressed(){
    theAlarm.turnOn();
  }
}
~~~

이렇게 변경이 가능합니다.

이렇게 되면 매번 버튼을 바꿔줄 때마다 코드를 변경해줘야 합니다.

이러면 OCP를 위반하게 되는 것이겠죠?!

확장에는 열려있고 수정에는 닫혀 있어야 하는 OCP 원칙 위배!!

기능을 호출하는 Button은 바뀌면 안됩니다.

따라서 이에 대한 해결책으로 클래스 다이어그램을 만들면?!

![그림8-2.PNG](/img/in-post/Software/그림8-2.PNG)<br>

이렇게 나옵니다.

기능을 호출하는 Command를 만들어서 set을 통해 Command를 설정해준 후에, 실행(pressed)!!!

이렇게 된다면, 새로운 기능이 추가되더라도, Client의 코드만 수정하면 되는 것입니다.

-> Button의 코드는 변함이 없겠죠?!

interface의 코드들을 구현해보겠습니다!

~~~
public interface Command{
  abstract public void execute();
}

public class Lamp{
  public void turnOn(){
    Systemout.println("Lamp!");
  }
}

public class LampOnCommand implements Command {
	private Lamp theLamp;
	public LampOnCommand(Lamp theLamp) {
		this.theLamp = theLamp ;
	}
	public void execute() { theLamp.turnOn() ; }
}

public class Alarm {
	public void start() { System.out.println("Alarming...") ; }
}

public class AlarmOnCommand implements Command {
	private Alarm theAlarm ;
	public AlarmOnCommand(Alarm theAlarm) {
		this.theAlarm = theAlarm ;
	}
	public void execute() { theAlarm.start() ; }
}

~~~

이런식으로 나오게 됩니다!

램프를 켜는 기능을 캡슐화를 했고, 알람을 울리는 기능을 캡슐화 했습니다!

결국 Command Pattern은

- 이벤트 발생 -> 실행될 기능이 다양하면서 변경이 필요한 경우

- 이벤트를 발생시키는 클래스의 변경없이 재사용하고자 할 때!!

- 호출자 클래스(Button) = Invoker

- 실제 기능을 실행하는 수신자 클래스 (Receiver) 사이의 의존성 제거!

- 따라서 기능의 변경에도 호출자 클래스(Button)를 수정 없이 그대로 사용!

#### Command Pattern

![그림8-4.PNG](/img/in-post/Software/그림8-4.PNG)<br>

1. Invoker = 기능의 실행을 요청하는 호출자 클래스

Ex) 리모컨

2. Command = 실행될 기느엥 대한 인터페이스. 실행 될 기능을 execute 메서드로 선언!

3. ConcreteCommand = 실제로 실행되는 기능을 구현

Ex) 채널 변경

4. Receiver = ConcreateCommand의 기능 실행을 위해 사용되는 수신자 클래스

Ex) Tv
