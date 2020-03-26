---
layout:     post
title:      "Linux nohup & background"
subtitle:   "명령어 설명 및 사용"
date:       2020-03-26 22:31:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Linux
tags:
  - Linux
---

## 환경

- Ubuntu 18.04

- XShell 6 (무료 버전)

## nohup이란? (간단한 설명)

- 쉘 스크립트 파일을 데몬 프로그램으로 실행시키는 프로그램

- 터미널과의 세션이 끊겨도 멈추지 않고 동작하게 하는 명령어

## 백그라운드 명령어 &

리눅스에서 작업을 할 때 **foreground** , **background** 로 나눌 수 있다.

**foreground** 는 간단히 말해서 명령어를 치고(& 제외), 실행시키는 것이 **foreground** 이다.

일반적으로 실행시키는 것은 다 **foreground** 이다.

하지만 **foreground** 로 실행시키면, 그 작업이 끝날 때 까지 아무런 작업을 하지 못한다.

- **foreground** 예시

- ls 명령어를 쳐도, 명령어가 실행되지 않는다.

![ping](/img/in-post/linux/ping.PNG)

따라서 오래 걸리는 작업이라면 **background** 로 실행시키는 것이 좋다.

**background** 는 '현재 보이지 않는' 곳에서(뒤에서) 실행되는 환경이다.

그렇기에 어떤 작업을 **background** 로 실행시키면 그 프로그램의 동작 여부의 상관 없이 다음 작업을 **foreground** or **background** 로 실행 시킬 수 있다.

- 백그라운드 명령어 **&** 예시

- ls 명령어가 실행되는 모습을 볼 수 있다.

- **[1]** 은 작업 번호, **17666** 은 PID 이다.

![ping](/img/in-post/linux/backgroundping.PNG)

![ping](/img/in-post/linux/backgroundpingPID.PNG)

**background** 명령어는 그 작업이 종료되거나, 사용자가 끄거나, 세션이 종료되면 끊긴다.

- 백그라운드 작업 확인 명령어 **jobs**

- **jobs** 명령어를 통해 현재 **background** 에서 실행되고 있는 작업 번호(**[1]**) 와 상태(**Running**), 작업명(**ping google.com &**) 을 알 수 있다.

![ping](/img/in-post/linux/jobs.PNG)

- 백그라운드 작업 종료 명령어 **kill -9**

- **kill %작업번호** 를 이용해 백그라운드에서 실행중인 작업을 끝낼 수 있다.

![ping](/img/in-post/linux/kill.PNG)

## nohup은?

앞에서 설명한 **background**, **foreground** 는 터미널과의 세션이 끊기면 작업이 다 종료가 된다.

하지만, 세션이 종료되어도 계속 실행시키고 싶은 작업이 있다면? (ex. Server)

이럴 때 **nohup** 명령어를 이용한다.

**nohup** 은 실행 중에 메시지를 출력할 곳이 필요하기 때문에 nohup.out 이라는 file을 만들어 실행중의 모든 메시지를 이 파일에 출력한다.

**nohup** 으로 실행된 작업을 종료하기 위해서는 **ps -ef | grep '작업명'** 을 이용해 PID를 알아낸 뒤에, **kill -9** 를 이용해 종료 시키면 된다.

- 다른 파일에 출력하기 **>**

**nohup echo Hello > ./hours22** 명령어를 입력하면 hours22 파일에 출력이 된다.

- 출력 안하기

**nohup echo Hello > /dev/null** 명령어를 입력하면 아무런 출력이 되지 않는다.

- 에러 출력하기 **2>**

**nohup echo Hello 2> ./hours22Errors** 명령어를 입력하면 hours22Errors 파일에 에러가 출력된다.

<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>


