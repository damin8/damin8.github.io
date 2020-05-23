---
layout:     post
title:      "new Instance에 Autowired Annotation 사용하기"
subtitle:   "Application Context"
date:       2020-05-24 22:31:00
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

## Autowired

spring framework 에서 제공하는 Annotation 인 **Autowired**

Spring Container에 등록한 클래스들을(Singleton 객체) 주입하는 Annotation이다.

지금까지 Container에 등록하고 싶은 클래스를 등록해주고, Bean으로 등록되는 클래스에서 **Autowired**를 사용하고 있었다.

따라서 new 생성자를 사용하지 않고, 의존성 주입을 통해 바로 사용해주는 것이다.

## 문제점

어느 날, 문제점이 발생했다.

지금까지는 Main Thread에서 Spring Container를 이용했기에 문제가 없었다.

프로젝트를 진행하던 도중, Thread 생성이 필요한 시점이 있었다.

하지만 Thread를 생성할때 new 생성자를 통해 사용해야 했다. (parameter가 필요했다)

따라서 자식 Thread를 Bean으로 등록할 수 없고, Autowired를 사용할 수 없었다.

그냥 사용한다면 의존성 주입이 안되기에 Null Pointer 오류가 난다.

그렇다고 Bean으로 등록되어 있는 클래스들을 new 생성자로 의존성 주입을 할 수도 없는 상황이고.. 참 난감했다.

## 문제점(사진)

- ThreadPool

![1](/img/in-post/Spring/threadpool.PNG)<br>

- Thread 실행

![1](/img/in-post/Spring/executorservice.PNG)<br>

- Autowired 

![1](/img/in-post/Spring/autowireNull.PNG)<br>

- Bean에 등록되어 있는 클래스

![1](/img/in-post/Spring/randmaker.PNG)<br>

- 의존성 주입이 안되는 상황

![1](/img/in-post/Spring/autowireNullPointer.PNG)<br>

## 해결 방법

- ApplicationContext(Spring IoC Container)를 관리 및 제공하는 클래스

~~~
@Component // Bean으로 등록
public class ApplicationContextProvider implements ApplicationContextAware {

    private static ApplicationContext applicationContext;

    // 인터페이스 구현부
    @Override
    public void setApplicationContext(ApplicationContext ctx) throws BeansException {
        applicationContext = ctx;
    }
    // 이 메서드를 통해 ApplicationContext(Spring IoC Container) 접근
    public static ApplicationContext getApplicationContext() {
        return applicationContext;
    }
}
~~~

- BeanUtils 클래스
- parameter로 클래스를 받아주기

~~~
@UtilityClass
public class BeanUtils {
    public static Object getBean(Class<?> classType) {
        ApplicationContext applicationContext = ApplicationContextProvider.getApplicationContext(); // Container 받아오기
        return applicationContext.getBean(classType); // Container에서 param의 class에 해당하는 bean 가져오고 return
    }
}

~~~

- 의존성 주입 (위의 코드로 예시)
- email, nickname은 무시
~~~
    private UserRepository userRepository;
    private RandMaker randMaker;
    private String email = null; 
    private String nickname = null;
    public CreateDummyUser(String email, String nickname){
        userRepository = (UserRepository)BeanUtils.getBean(UserRepository.class); // param에 class를 넣어주기 (형변환)
        randMaker = (RandMaker)BeanUtils.getBean(RandMaker.class); // 위와 동일
        this.nickname = nickname;
        this.email = email;
    }
~~~

- 의존성 주입 (성공😊)

![1](/img/in-post/Spring/autowiredSuccess.PNG)<br>


## 결론

- new로 생성한 instance를 사용하는 경우가 있다

- 그럴 경우 위의 해결 방법을 이용하면 된다

## Reference

[New Instance 의존성 주입](https://jeong-pro.tistory.com/174)

<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>


