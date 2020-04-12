---
layout:     post
title:      "IntelliJ로 Servelt&JSP 환경 구성하기"
subtitle:   "Tomcat Web 환경 구성"
date:       2020-04-12 22:31:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Servlet_JSP
tags:
  - Servlet_JSP
---

## 환경

- JDK 1.8
- Tomcat 9

## 개발 환경 구성

개발을 시작하기 앞서 개발 환경 구성이 선행이 되어야 한다.

바로 개발 환경을 구성해보자.

![IntelliJ1.PNG](/img/in-post/Servlet_JSP/IntelliJ1.PNG)

- Create New Project 선택

![IntelliJ2.PNG](/img/in-post/Servlet_JSP/IntelliJ2.PNG)

- 상단에 Project에 적용할 JDK 선택 (1.8)
- WebServices 클릭 후, **Apache Axis** 선택

- 다음은 자신이 원하는 project 이름(까먹고 사진 첨부를 못했습니다 ㅠ)

![IntelliJ2.PNG](/img/in-post/Servlet_JSP/IntelliJ3.PNG)

- SoapUI Download? 창이 뜰 텐데 가볍게 무시.

![IntelliJ2.PNG](/img/in-post/Servlet_JSP/IntelliJ4.PNG)

- 만들었을 때 초기 화면 (상단 부분만 캡처)
- 빨간색 밑줄 친 부분 클릭

![IntelliJ2.PNG](/img/in-post/Servlet_JSP/IntelliJ6.PNG)

- **configure**를 통해 Download 되어 있는 자신의 tomcat 경로 넣어주기
- OpenBrowser를 통해 자신의 web Server의 default browser를 골라준다
- HTTP Port를 통해 자신이 원하는 port 설정! (저는 8080!)





<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>


