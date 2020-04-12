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

나도 까먹지 않고, 팀원들을 위해 작성해보자.

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

![IntelliJ5.PNG](/img/in-post/Servlet_JSP/IntelliJ5.PNG)

- Tomcat 경로 넣는 부분 참고!

![IntelliJ5.PNG](/img/in-post/Servlet_JSP/IntelliJ7.PNG)

- Deployment를 클릭해서 application context를 /로 바꿔주자
- 기본 경로를 /로 바꿔주기 위함.

> 만약 war exploded 가 없다면, 오른쪽에 있는 + 버튼을 눌러 artifact를 만들어주면 된다.

## 테스트

이제 기본 세팅은 다 끝났다.

테스트를 해서 환경 세팅이 끝났나 확인해보자.

![IntelliJ5.PNG](/img/in-post/Servlet_JSP/IntelliJ8.PNG)

> 만약 add Configuration으로 잡혀 있다면 클릭한 후에 우측 상단에 create configuration 을 누르면 완료~!

- index.jsp 파일로 이동해서 실행시켜보자. (우측 상단 초록색 화살표 버튼)

> 단축키는 Alt + F10

![IntelliJ5.PNG](/img/in-post/Servlet_JSP/IntelliJ9.PNG)

잘 되는 것을 확인했다.

<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>


