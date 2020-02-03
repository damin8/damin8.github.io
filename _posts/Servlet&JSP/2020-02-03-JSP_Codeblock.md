---
layout:     post
title:      "JSP Code Block"
subtitle:   "종류와 의미"
date:       2020-02-03 21:17:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Servlet&JSP
tags:
  - Servlet&JSP
---

## JSP의 Code Block

- JSP 파일에 코드를 입력하면 JSP 클래스의 JSP Service 메서드에 들어가게 된다. 

- JSP에서는 Code Block을 씌우지 않으면 JSP Service 메서드에서 out.write() 메서드를 통해 출력하게 된다.

- 따라서 html 문서와 code를 분리하기 위해 Code Block을 이용한다!

### <% %>

~~~
<%
  int x;
  int y;
%>
~~~

- <% %> 를 사용하게 된다면 일반적으로 출력하는 것이 아닌 Code로 인식

- 출력 x

### <%= %>

~~~
z의 값은 <%=x+y%>
~~~

- <%= %>를 이용하여 모든 부분을 Code로 인식하는 것이 아니라 부분적으로 Code로 인식하게 사용한다 

- out.write + out.print

### <%! %>

~~~
<%!
  public int sum(int x,int y)
  {
    return x + y;
  }
%>
~~~

- 그냥 Code Block을 씌우게 되면 Service 메서드 안에 또 메서드가 생기는 것이다.

- 따라서 에러 발생!

- <%! %> 을 이용해 JSP 클래스의 멤버 메서드로 만들어 준다.

### <%@ %>

~~~
<%@ page language="java" contentType="text/html; charset=UTF-8"
  pageEncoding="UTF-8" %>
~~~

- 일반적으로 Code Block이라 부르지 않는다.

- Page 지시 블럭 이라고 부른다.

- pageEncoding="UTF-8" -> 사용자에게 UTF-8로 출력해라

- contentType="text/html; charset=UTF-8" -> 웹 브라우저에게 알려주기 위함

- 가장 먼저 실행이 된다
