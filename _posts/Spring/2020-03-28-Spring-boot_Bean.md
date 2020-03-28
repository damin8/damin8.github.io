---
layout:     post
title:      "Spring boot Bean"
subtitle:   "About Bean"
date:       2020-03-28 22:31:00
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

## Spring & Bean

Bean을 설명하기에 앞서 Spring에 대해 알아보자.

Spring은 경량 컨테이너로서 자바 객체를 직접 관리한다.

객체의 생성, 소멸과 같은 Life Cycle을 관리하며 Spring Container에서 필요한 객체를 얻을 수 있다.

처음에 무슨 말인지 몰랐다. 그냥 **"아.. 그렇구나~"** 하고 넘어갔다.

요즘 Spring framework를 계속 사용하면서 Spring framework가 무엇인지 조금씩 알아가는 느낌이 든다.

잡소리는 그만하고, 이게 무슨 말인지 잘 모르겠는 사람들을 위해 예를 들어 보자.

- 일반적인 JAVA

~~~
public class Calculator{

  public int sum(int x,int y){
    return x+y;
  }
}
~~~

---

~~~
public class Shop(){
  private int apple = 500;
  private int banana = 600;
  
  public int total(){
    Calculator calculator = new Calculator();
    return calculator.sum(apple,banana);
  }
}
~~~

보통의 경우 다른 클래스에서 Calculator를 사용하기 위해서는 해당 클래스에서 직접 new 생성자를 통해 만들어 줘야 한다.

Calculator라는 객체는 new 를 통하여 만들어지지 않는다면, 없는 것과 마찬가지다.

- Spring-boot

~~~
@Component
public class Calculator{

  public int sum(int x,int y){
    return x+y;
  }
}
~~~

---

~~~
public class Shop(){
  private int apple = 500;
  private int banana = 600;
  
  @Autowired
  Calculator calculator
  
  public int total(){
    return calculator.sum(apple,banana);
  }
}
~~~

딱 봐도 다르다.

의아할 수 있다. **"어떻게 calculator를 생성하지도 않고 calculator 객체를 사용하지?"**

Spring Container에서 Annotation(@Component)를 확인하고 자동으로 Bean 객체를 생성해서 Spring Bean으로 등록 된다.

Shop Class 내부에 있는 calculator는 Spring Container에 등록된 Calculator 객체를 가져와 주입을 한 것이다.

이렇기에, 위의 코드가 가능한 것이다.

Bean과 Java 일반 객체와 차이점은 없다. Spring Container에 의해 만들어진 객체를 그냥 Spring Bean이라고 부를 뿐이다.

## Bean Annotaion 종류

Spring-boot의 경우 @Component, @Service, @Controller, @Repository, @Bean, @Configuration 등등으로 필요한 Bean을 등록한다.

Bean으로 등록하고, 다른 Class에서 @Autowired 어노테이션을 통해 주입하는 것이 일반적이다.

> Spring 2.x 버전 이상부터는 생성자 parameter가 Bean객체로 등록되어 있으면 @Autowired를 사용하지 않고도 의존성 주입을 해준다고 한다.



<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>


