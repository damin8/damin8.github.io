---
layout:     post
title:      "Spring Boot"
subtitle:   "Gradle 기반 Spring war 파일 배포"
date:       2020-02-26 18:17:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Spring
tags:
  - Spring
---

Spring Boot 에서는 확장자를 'jar'로 배포 하면 JSP 사용이 불가하고 webapp 폴더를 무시한다고 한다🤢

'war' 는 별도의 내장 서버를 사용하지 않고 외장 서버에 배포할 수 있다!

'war' 확장자로 배포하는 방법을 알아보자😊

## 1. 프로젝트 생성

![1](/img/in-post/Spring/1.PNG)<br>

- Spring boot 프로젝트를 만들기 위해 starter project 생성!!

- 빨간색으로 표시된 부분 (gradle, war)로 설정!

- 'war'로 선택하면 ServletInitializer.java 라는 파일 생성!

## 2. 코드

- 기존과 다르게 SpringBootTestApplication.java를 사용하지 않는다 -> 주석 or 삭제

![2](/img/in-post/Spring/2.PNG)<br>

- ServletInitializer class에 **@SpringBootApplication** 어노테이션 추가

- configure 함수의 코드도 위와 같이 수정

- main 함수 정의

## 3. gradle 설정

- plugin을 설정해 주자

~~~
plugins {
  id 'war'
}

or

apply plugin : 'war'
~~~

- 'war' 생성관련 설정 가능 (Default : 프로젝트명 + Version)

~~~
bootWar{
  archiveBaseName = '원하는 이름'
  archiveFileName = '원하는 이름.war'
  archiveVersion = "0.0.0(예시)"
}
~~~

- 외부 톰캣 사용한다는 providedRuntime 설정

~~~
providedRuntime 'org.springframework.boot:spring-boot-starter-tomcat'
~~~

- 이미 있다면 그대로

## 4. 실행

![3](/img/in-post/Spring/3.PNG)<br>

- 실행하면 이런 화면이 뜬다.

## 5. 'war' 파일 만들기

- 원하는 프로젝트 위치로 이동한다.

> 모른다면 '프로젝트 오른쪽 클릭 -> properties -> 왼쪽에 resource -> location에 있는 화살표'

- 프로젝트 위치로 이동했다면 'gradlew' 라는 파일이 있을 것이다.

- 이걸 이용해서 만들어 보자.

- cmd(실행)창을 켜서 프로젝트 위치로 'cd(change directory)' 명령어를 이용해 이동하자

- 'gradlew bootWar' 명령어를 이용해 빌드하자

![5](/img/in-post/Spring/5.PNG)<br>

- 성공했다면 (프로젝트명/build/libs) 디렉터리로 이동해 war파일이 만들어 졌는지 확인!

![6](/img/in-post/Spring/6.PNG)<br>

- 다음에는 다시 cmd(실행)창을 켜서 이 war파일이 있는 위치로 이동

- 'java -jar Example.war' 를 이용해 실행시키자!

![7](/img/in-post/Spring/7.PNG)<br>


- 이런 창이 뜨면 성공👍

#### Reference

[Spring Boot Gradle War 배포](https://gigas-blog.tistory.com/115)

