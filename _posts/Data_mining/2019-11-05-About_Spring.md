---
layout:     post
title:      "Spring 이란?"
subtitle:   "Spring의 개념"
date:       2019-11-05 18:17:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Spring
tags:
  - Spring
---

# About Spring

흔히들 스프링이라고 부른다.

원래는 "스프링 프레임워크" 라고 하는 것이 정확한 표현이다.

자바 플랫폼을 위한 오픈소스 애플리케이션 프레임 워크.

- Dependency injection, Transaction management

~~~

-> 일반적인 software를 만들 때는 중요하지 않을 수 있다.

-> enterprise 에서는 이 두가지가 중요해 진다.

-> Transaction 은 Java EE에서도 제공을 하지만, 복잡해진다

-> Spring에서는 Transaction management 를 라이브러리로 제공

-> Dependency injection 까지 편리하게 제공

-> 따라서 훨씬 편리

-> 점점 Java EE 영역을 조금씩 갉아 먹고 있다

~~~

어느 순간 Java SE 위에 Java EE 대신에 Spring을 올린다.

1. MVC <- DI <- 느슨한 결합력과 인터페이스

2. 트랜잭션 <- AOP

3. 인증과 권한 <- Servlet Filter


