---
layout:     post
title:      "AWS Ubuntu 시간 변경"
subtitle:   "AWS EC2"
date:       2020-01-30 21:43:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Linux
tags:
  - Linux
---

# AWS Ubuntu 시간 변경

AWS EC2 Ubuntu를 사용하여 PC 관리 프로젝트인 **System-monitor**의 서버를 올렸다.

![region](/img/in-post/linux/region.png)

Region을 서울로 설정하고 인스턴스를 생성했는데 Timezone이 UTC 였다.

![Default_Time](/img/in-post/linux/ubuntu_time.png)

하지만 Server와 http 통신을 위해 Timezone이 Seoul 이어야 했다.

#### AWS Ubuntu Timezone을 바꿔 보자!
---
~~~
timedatectl list-timezones
~~~

- 변경 가능한 timezone 나라와 도시가 list로 뜬다.

![Default_Time](/img/in-post/linux/timezone_list.PNG)

---
~~~
timedatectl list-timezones | grep 'Seoul'
~~~

- 모든 도시를 볼 수 없으니 grep 명령어를 사용하여 원하는 문자열(Seoul)을 찾자!

![Default_Time](/img/in-post/linux/Seoul.PNG)

- 목록에 Seoul이 있다면 변경 가능!

---

- 바꾸기 명령어
~~~
timedatectl set-timezone Asia/Seoul
~~~

---

- 실행 결과

![Default_Time](/img/in-post/linux/TimezoneResult.PNG)

### Reference

[AWS Ubuntu 시간 변경하기](https://brtech.tistory.com/92)
