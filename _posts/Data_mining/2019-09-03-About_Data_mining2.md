---
layout:     post
title:      "Data mining 이란? -2"
subtitle:   "Data mining의 개념"
date:       2019-09-03 18:17:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: web
tags:
  - Data mining
---

## Agent의 output

### Rule

Classification rule (분류 규칙)

-> 속성들로 하여금 클래스에 대한 예측

Association rule (연관 규칙)

-> 어느 속성이던 상관없이 상호 연관성을 만들고, 그에 대한 예측

> 클래스에 대한 예측도 연관 규칙이 될 수 있다.

### decision tree

일반적인 rule과 다른점

-> 계층의 비교가 순서적으로 이루어 진다(위에서 부터)
-> root는 정보 분류 능력이 가장 큰 것

### deployment

new data가 계속 들어가서, incremental(점진적)이다.

> adaptation(update)

Instance(행) = attribute + class

Clustering : 여기저기 퍼져있을때, 군집 되어 있는 것들

Supervised : hard or soft, yes or no, etc...
(명시적) target 값에 대한 것

nominal한 값에 대해서만 연관 관계

numeric을 다 비교할 수 없기 때문에

Cluster(군집)은 명시적이지 않다.

### Clustering

군집하다 보면, 포함되지 않는 데이터도 생긴다.

new data(instance)가 n차원 속성 공간에 position 되면, 그 군집에 있는 것으로 바로 추천을 하게 된다.

Instance-based learning (예제 기반 학습)

새로운 instance가 input으로 들어오면, 그 instance를 다 비교해준다.

만약 Knowledge에 있는 instance가 많다면, 시간이 오래걸린다.

따라서 Instance-based learning은 오래걸린다.

반면에 clustering은 그냥 그 군집에 있는것을 바로 recommendation을 해주기 때문에

예제기반 학습보다 빠르다.

### Instance

Instance 2개를 같이 처리 해줄 수 없다.

> 기계학습 알고리즘이 다양하기 때문에

Instance는 각각 독립적이다(개별적이다)


