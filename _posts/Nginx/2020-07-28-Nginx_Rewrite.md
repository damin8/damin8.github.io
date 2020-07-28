---
layout:     post
title:      "nginx rewrite"
subtitle:   "nginx rewrite"
date:       2020-07-28 16:31:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Nginx
tags:
  - Nginx
---

## 환경

- Ubuntu 18.04

## 상황

Nginx 를 reverse proxy 로 사용하고 있다

Test Server를 구축해서 같은 Ubuntu에 띄우려고 했다

<code>/test/user or main/~~~</code> 의 요청이 들어오면

<code>/user or main/~~~</code> 의 요청으로 바꿔줘야 했다


## 해결

```nginx
location /test/user{
                rewrite ^/test(.*)$ $1 break;
                proxy_pass "http://localhost:1111";
        }  
location /test/main{
                rewrite ^/test(.*)$ $1 break;
                proxy_pass "http://localhost:1112";
        }  
```
- 각 location 에 <code>rewrite ^/test(.*)$ $1 break</code> 구문 추가

- /test 이후로 오는 URI로 다시 쓰겠다 -> $ 로 칭한다

- $1 = 위의 값을 가르킨다

> ex) localhost:9999/test/user/find/all -> localhost:1111/user/find/all

- 적용한 후에 꼭 nginx를 reload 해줘야 한다 (이거 때문에 삽질했다...)

- <code>nginx -s reload</code>


<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>
