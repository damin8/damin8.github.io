---
layout:     post
title:      "Overriding, Overloading"
subtitle:   "둘의 차이점"
date:       2020-02-03 19:00:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Java
tags:
  - Java
---

## Overriding

- 관례적으로 메서드 위에 **@Overriding**을 적어줌.

- 상위 클래스가 가지고 있는 메서드를 재정의 하여 다르게 사용하기 위함.

- 상위 클래스의 메서드와 반드시 parameter가 같아야 한다.

- 상위 클래스의 메서드와 반드시 return type이 같아야 한다.

![OverridingTest](/img/in-post/Java/OverridingTest.PNG)

### Overriding parameter가 다른 경우

![OverridingTest2](/img/in-post/Java/OverridingTest2.PNG)

## Overloading

- 같은 이름의 메서드를 매개변수에 따라 다르게 메서드를 사용하기 위함.

- 메서드마다 parameter가 다르다.

- 메서드마다 return type이 다를 수도 있다. (같아도 된다)

![OverloadingTest](/img/in-post/Java/OverloadingTest.PNG)

<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async> </script>
