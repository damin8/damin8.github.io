---
layout:     post
title:      "MongoDB Command"
subtitle:   "기본 Command 모음집"
date:       2020-03-21 22:31:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: MongoDB
tags:
  - MongoDB
---

MongoDB Ver3.6

## 계정 생성

그냥 자유롭게 User,Pwd 를 설정하지 않고 사용할 수 있다.

하지만, 이렇게 된다면 보안에 매우 취약할 것이다.

> 원격접근이 자유롭다 -> 취약하다

따라서 계정을 생성하여 User와 Pwd를 만들어서 기본적인 보안을 갖춰보자.

### Admin 계정 생성

~~~
use admin (admin DB가 없다면 만들어주고, 있다면 admin DB를 사용한다.)

db.createUser({
  user : "계정 이름",
  pwd : "계정 비밀번호",
  roles : ["dbAdminAnyDatabase"]
  })
~~~

### DB 계정 생성

각 데이터 베이스용 계정 생성을 해보자

2가지 방법이 있다.

1. 계정을 생성할 DB에 접근하여 만드는 방법.

~~~
use Laptop (DB 이름)

db.createUser({
  user : "계정 이름",
  pwd : "비밀번호",
  roles : ["readWrite"] (읽기와 쓰기를 하겠다.)
~~~

2. 위치 무관 계정 생성하기.

~~~
db.createUser({
  user : "계정 이름",
  pwd : "비밀번호",
  roles : ["readWrite", db:"Laptop"] (읽기와 쓰기를 하겠다.)
~~~

만약 "Laptop" 이라는 DB가 없다면 만들어 준다.

### DB 계정 삭제

admin DB의 위치에서 명령을 실행시키면 된다.

~~~
use admin (admin으로 이동)

db.dropUser("계정 이름")
~~~

---

계정을 생성했으니, 본격적으로 DB의 관련된 명령어를 알아보자.

### DB 조회

![db](/img/in-post/MongoDB/db.PNG)<br>

- db : 현재 사용중인 데이터 베이스 확인

![db](/img/in-post/MongoDB/showdbs.PNG)<br>

- show dbs : DB 리스트 확인

![db](/img/in-post/MongoDB/dbstats.PNG)<br>

- db.stats() : 현재 DB 상태 확인

### DB 삭제

![db](/img/in-post/MongoDB/drop.PNG)<br>

- db.dropDatabase() : DB 삭제

> 삭제하고 싶은 DB로 이동(use) 후에 실행 해야 한다.

### Collection (RDB에서 Table이라고 생각하면 된다.) 생성

![db](/img/in-post/MongoDB/createcollection.PNG)<br>

- db.createCollection("테이블 이름", {options})

option

1. capped : Boolean 타입. true로 설정하면 자신의 table이 설정한 size를 초과할 경우 오래된 데이터를 덮어쓴다.

> true로 설정하면 꼭 size를 설정해야 한다.

2. size : Number 타입. 해당 Collection의 최대 사이즈를 ~bytes로 지정

3. max : Number 타입. 해당 Collection에 추가 할 수 있는 최대 Document 갯수를 설정.

### Collections 조회

![db](/img/in-post/MongoDB/showcollection.PNG)<br>

- show collections : DB의 Collection 리스트 조회.

### Collection 제거

![db](/img/in-post/MongoDB/collectiondrop.PNG)<br>

- db.원하는 Collection.drop() : 원하는 Collection 을 제거한다.

### Collection 이름 변경

![db](/img/in-post/MongoDB/changecollection.PNG)<br>

- db.OLDSamsung.renameCollection("NEWMac") : 이름 변경

<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>


