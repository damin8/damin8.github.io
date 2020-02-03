---
layout:     post
title:      "Servlet Class 상속"
subtitle:   "Get, Post 요청 처리하기"
date:       2020-02-03 18:17:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Servlet&JSP
tags:
  - Servlet&JSP
---

## Servlet Class 상속

어떤 클래스를 만들 때, HttpServlet 클래스를 상속 받아서

Get 요청과 Post 요청 처리를 다르게 하고 싶다면

### 첫 번째 방법

![doGet_Post](/img/in-post/Servlet_JSP/doGet_Post.PNG)

- req을 이용하여 요청 온 것이 GET인지 POST인지 확인한다.

- if 문으로 나눠서 Get 요청과 Post 요청을 나눠서 처리하면 된다.

- 반드시!!! super.service를 주석처리 해야 한다.

~~~
왜? super.service에는 doPost 와 doGet 메서드를 호출한다. 

그런데 doPost와 doGet이 Override 되지 않았기 때문에 오류가 난다.
~~~

### 두 번째 방법

![doGet_Post2](/img/in-post/Servlet_JSP/doGet_Post2.PNG)

- 부모의 Service를 활용하자!

- doGet과 doPost를 Override 하여 요청을 처리해준다.
