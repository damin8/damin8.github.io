---
layout:     post
title:      "Java Thread"
subtitle:   "Thread join"
date:       2020-03-05 13:17:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Java
tags:
  - Java
---

# Thread

대학교를 입학한지 얼마 안됐을 때, 개발을 해 본적도 없고 완전 무지한 상태에서 Thread에 대해 수업을 들었을 때가 기억이 난다.

그때는 무슨 소린지 하나도 모르고 중요하지도 않았다고 생각 했었다.

요즘 진행중인 Project에서 Thread 분리를 해야 하는데 여기서 Thread에 대해 예전 보다는 많이 알게 되었고

Thread에 대해 생각하는 Project를 하게 되어서 다행이고 고맙고 좋다.

오늘 Project를 하던 중에 Thread에 대해 하나 더 배운 것이 있어서 까먹지 않게 작성을 하려고 한다.

상황은 이렇다.

1. A Class의 B Method를 실행한다. (Main Thread가 아닌 Sub Thread)

2. C Class의 D Method를 실행한다. (단, A Class의 B Method가 끝난 후에 Sub Thread로 실행)

내가 머리가 아팠던 부분은

Sub Thread에 있는 B Method를 어떻게 끝났는지 안끝났는지 알 수 있지? 라는 부분이었다.

인터넷을 찾아보던 도중 Thread.join() Method를 알게 되었다.

~~~
public class PostLongPolling extends Thread {
	PC pc = null;

	public PostLongPolling(PC pc) {
		this.pc = pc;
	}

	public void run() {
		try {
			System.out.println("Two");
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}

	public static void main(String[] args) {
    Pc pc = new Pc();
		Thread PostLongPollingThread = new PostLongPolling(pc);
    System.out.println("One");
    try {
			PostGeneralThread.start();
			PostGeneralThread.join();
      System.out.println("Three");
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
	}
  
  // 출력 결과 : One
                 Two
                 Three
            
~~~

join을 이용하면 Thread가 끝날 때 까지 기다릴 수 있다.

물론 join 없이 실행 되더라도 One Two Three 가 뜰 수도 있다.

하지만 너무 불안전하고, 랜덤이기 때문에 Thread 안에 있는 join Method를 사용하여 Thread를 관리해 주자!

<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>
