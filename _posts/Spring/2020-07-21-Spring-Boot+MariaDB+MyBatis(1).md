---
layout:     post
title:      "Spring Boot + MariaDB + MyBatis (1)"
subtitle:   "Ubuntu에 MariaDB 설치"
date:       2020-07-21 22:31:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Spring
tags:
  - Spring
  - MariaDB
  - MyBatis
---

## 환경

- Spring Boot 2.2.5
- Ubuntu 18.04
- MariaDB

## 잡다한 이야기

[DEVSTU](https://devstu.co.kr/) 프로젝트를 시작하기 전에 DB에 관해서 관계형, 비관계형 DB 중에 골라야 했다.

우리는 비관계형을 골랐고 MongoDB 를 선택했다.

프로젝트를 6개월 이상 진행했고 어느 정도 시중에 출시?할 정도 완성됐다.

하지만, 문제는 하다보면서 계속 참았지만 

우리의 프로젝트는 **비관계형 DB 와 맞지 않다!** 라는 결론이 나왔다.

이제라도 MongoDB -> MariaDB로 넘어가는 작업을 하고 있다.

이렇게 넘어가는 시점을 기준으로 기록을 남기고 싶어 쓴다.

## Ubuntu에 MariaDB 설치

내 컴퓨터의 OS는 Window이다.

하지만 Ubuntu에 있는 DB로 접근을 할 것이기 때문에 (외부에서 접속) Ubuntu에 MariaDB를 설치할 것이다.

자신이 Local에서만 실행할 것이라면 Local 컴퓨터 OS의 맞게 MariaDB 설치👨

---

```
sudo apt-get install -y mariadb-server
```

> install -y = 모든 조건에 yes를 하겠다는 의미

위 명령어를 이용해 설치하자.

설치 끝👍

## MariaDB 환경 설정

- /etc/mysql/mariadb.conf.d/50-server.cnf 파일을 수정하자.

```
sudo vi /etc/mysql/mariadb.conf.d/50-server.cnf
```
1번 사진
![1](/img/in-post/Spring/vi1.PNG)

2번 사진
![1](/img/in-post/Spring/vi2.PNG)

1번 사진으로 되어 있을텐데 2번 사진으로 수정

- /etc/mysql/mariadb.conf.d/50-client.cnf 파일을 수정하자.

```
sudo vi /etc/mysql/mariadb.conf.d/50-client.cnf
```

1. default-character-set = utf8mb4 주석 처리 (#을 이용해 주석처리 할 수 있다.)

1. default-character-set=utf8 밑에다 바로 추가

![1](/img/in-post/Spring/vi3.PNG)


- 세팅을 다 해줬으니 재시작

```
service mysql restart
```

## MariaDB 접속 및 계정 생성

```
# mysql root로 접근 (초기 비밀번호는 없다 -> 그냥 엔터치고 접속)
mysql -u root -p

# DB 확인
show databases;

use mysql;

# user table에서 host,user,password를 출력
select host,user,password from user;

# root 비밀번호 바꾸기
update user set password=password('비밀번호') where user='root';

# 외부에서 접근 가능한 user 생성하기
# ex) create user '22hours'@'%';
create user '생성할 ID'@'%';

# password 설정하기
# ex) update user set password=password('1234') where user='22hours';
update user set password=password('***') where user='생성할 ID';

# 모든 것을 할 수 있는 권한 주기
# ex) grant all privileges on *.* to '22hours'@'%';
grant all privileges on *.* to '생성할 ID'@'%';

# 변경 사항 적용
flush privileges;
 
```

이렇게 하면 환경설정이 다 끝났다.

다음시간 👨‍💻

- Spring boot 와 MariaDB 연동 (feat.MyBatis)

## Reference

[Ubuntu MariaDB 설치](https://nowonbun.tistory.com/423)

<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>


