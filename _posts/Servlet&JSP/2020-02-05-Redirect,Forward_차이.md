---
layout:     post
title:      "Redirect vs Forward"
subtitle:   "Redirect 와 Forward 차이"
date:       2020-02-05 02:45:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Servlet_JSP
tags:
  - Servlet_JSP
---

- Redirect, Foward 둘 다 현재 작업중인 페이지에서 다른 페이지로 전환하는 기능

- URL : 맘스터치

- Client : 손님

- Server : 직원

# Redirect 사례

- 손님(Client)를 맘스터치(URL)을 방문한다.

- 손님이 직원(Server)에게 "상하이 스파이시 버거"를 주문한다.

- 맘스터치에는 "상하이 스파이시 버거"가 없다.

- 따라서 직원은 손님에게 "손님 '상하이 스파이시 버거'는 '맥도날드'(다른 URL)에 있습니다~" 라고 응답한다.

- 손님은 다른 매장 '맥도날드'로 간다.

### Redirect 특징

- web container는 redirect 명령이 들어오면 웹 브라우저에게 다른 페이지로 이동하라는 명령을 내린다

> '맘스터치'에서 '맥도날드'로 가라고 한다.

- 웹 브라우저는 URL을 지시된 주소로 바꾸고 그 주소로 이동한다.

- 다른 web container에 있는 주소로 이동이 가능하다.

> '맘스터치' -> '맥도날드'

- 새로운 페이지에서는 request, response 객체가 새롭게 생성된다.

> 손님은 '맥도날드'를 가서 다시 '상하이 스파이시 버거'를 주문해야 한다.


# Forward 사례

- 손님(Client)를 맘스터치(URL)을 방문한다.

- 손님이 직원(Server)에게 '불고기 버거'를 주문한다.

- 손님이 직원에게 "불고기 패티 1장 더 주세요" 라고 요청한다.

- 직원이 주방 직원에게 "방금 들어간 주문 패티 1장 더 주세요~" 라고 요청한다.

- 주방에서 패티가 2장인 '불고기 디럭스 버거'가 나온다.

### Forward 특징

- 같은 web container 차원에서의 페이지 이동 

> 같은 맘스터치 매장에서 다른 메뉴로 이동

- 실제로 웹 브라우저는 다른 페이지로 이동했는지 알 수 없다

> 손님은 '불고기 디럭스 버거'인지 모른다

- 웹 브라우저에서는 최초 호출한 URL만 표시되고, 이동한 페이지의 URL 정보는 볼 수가 없다

> 주방에서 메뉴를 바꾼 것을 손님은 모른다

- 현재 실행중인 페이지와 forward에 의해 호출될 페이지는 request, response 객체를 공유한다 

> 손님이 요청한 사항은 손님이 메뉴를 받을 때 까지 유효하다

- forward 방식은 다음 이동한 URL로 요청 정보를 그대로 전달한다.

- 말 그대로 forward(건네주기) 하는 것이다.

---

### 정리

1. URL 변화 여부

Redirect = 변화 ⭕

Forward = 변화 ❌

2. 객체 재사용 여부

Redirect = 재사용 ❌

Forward = 재사용 ⭕

- 이러한 특징들 때문에 웹 애플리케이션 작성할 때 적절히 사용하여야 한다.

- 카페 게시판에 글 쓰기를 할 때, 이 페이지는 forward로 작성해야 할까? redirect로 작성해야 할까?

> redirect 이다.

- 새로 고침을 하게 된다면 forward의 경우 요청정보가 살아있기 때문에 똑같은 글이 여러번 등록될 수 있다.

- 하지만 redirect의 경우 요청 정보가 존재하지 않는다.

- 시스템에 변화가 생기는 요청의 경우 = redirect

- 변화가 생기지 않고 단순 조회의 경우 = forward


