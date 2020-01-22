---
layout:     post
title:      "Data mining 이란? -2"
subtitle:   "Data mining의 개념"
date:       2019-10-10 20:11:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Data_mining
tags:
  - Data mining
---

# Covering algorithm

분류 능력을 최대화 시키자!

1. 가능한 많은 같은 Instance들을 포함하게!!!

2. 가능한 다른 Instance들을 배척하게!!

![covering_algorithm](/img/in-post/Data_mining/covering_algorithm.PNG)<br>

처음에 나눴을 때 오른쪽에 아직 b가 많이 남아 있습니다.

두 번째에 1번,2번을 적용하여 최대한 같은 Instance가 포함되게 나누고, 최대한 다른 Instance를 배척하였습니다

Decision Tree = Instance에 대한 속성, 속성값에 집중

Covering algorithm = 각각의 class에 집중!!

![coverrule](/img/in-post/Data_mining/coverrule.PNG)<br>

이제부터 weather domain 기준으로 보자!!

각각의 class C (ex. play=yes) 에 대해

E 를 Instance set으로 초기화 한다

E = 9개의 yes (weather domain -> yes = 9, no = 5)

왼쪽 condition을(LHS) empty로 두고 기본적인 rule을 만들자

if (empty), then "play = yes"

이 룰을 완성시켜보자.

R이 완전해질 때까지 각각의 attribute A의 value 에 대해 (아직 언급되지 않은) 반복!!

ex) outlook attribute가 나왔다면 그 다음 조건문에는 outlook을 제외!

p/t가 가장 큰 값을 고른다.

> p(positive examples) / t(instances)

만약 둘의 값이 같다면 p가 큰 것으로 고른다!

> 2/4 = 4/8 인데 p가 4가 더 크기 때문에 4/8 선택!

조건이 완성되면 E에서 그에 맞는 것을 지운다!

만약 1,2,3,4,5,6 번째 Instance가 yes라면

E = 1,2,3,4,5,6

조건문에 맞는 E = 1,2,3,4

then E = 5,6

하지만 6개의 Instance를 다 찾지 않았으므로 나머지 5,6을 찾을때 까지 반복

Contact lens 를 보자

![contact](/img/in-post/Data_mining/contact.PNG) <br>

recommendation = "hard" 인 것 중에

Age = young = 2/8 (young의 hard 개수 / young의 recommendation 개수)

이렇게 p/t 를 구한 후에 가장 큰 값을 고른다.

![contact2](/img/in-post/Data_mining/contact2.PNG) <br>

다음 단계에서 astigmatism = yes 를 제외한 instance에서 고른다

Age = young = 2/4 (young의 astigmatism = yes를 제외한 hard의 개수 / young의 astigmatism = yes를 제외한 개수)

이 과정을 perfect 해지기 전 까지 반복한다.

~~~
if (empty) then recommendation = "soft" 를 완성 시켜보자!

E = 2, 6, 10, 14, 22

1단계

Age = young, 2/8
    = pre-presbyopic, 2/8
    = presbyopic, 1/8
    
Spectacle prescription = myope , 2/12
                       = hypermetrope, 3/12
                       
Astigmatism = no, 5/12
            = yes, 0/12
            
Tear production rate = reduced, 0/12
                     = normal, 5/12

Astigmatism = no, 5/12 와 Tpr = normal, 5/12 로 동률이다.

Astigmatism 으로 고르겠습니다.

2단계

if Astigmatism = yes And ? then recommendation = soft

Age = young, 2/4
    = pre-presbyopic, 2/4
    = presbyopic, 1/4
    
Spectacle prescription = myope , 2/6
                       = hypermetrope, 3/6
                       
Tear production rate = reduced, 0/6
                     = normal, 5/6

Tpr = normal, 5/6이 가장 크기 때문에 Tpr 선택!

3단계

if Astigmatism = yes And Tear production rate = normal And ? then recommendation = soft

Age = young, 2/2
    = pre-presbyopic, 2/2
    = presbyopic, 1/2
    
Spectacle prescription = myope , 2/3
                       = hypermetrope, 3/3

Sp = hypermetrope, 3/3 (perfect!) 로 Sp 선택!

Perfect 하기 때문에 다른 attribute는 일단 그만 보자.

이를 통해 나온 식

if Astigmatism = yes And Tear production rate = normal 
And Spectacle prescription = hypermetrope then recommendation = soft (6, 14, 22)

E 에 있는 6, 14, 22 를 지우자!

이제 E = 2, 10 이 남았다.

아직 끝난게 아니다. 왜? E가 아직 남았기 때문이다.

처음부터 다시 돌아가서 하는데, 이미 지워진 E 의 Instance는 제외하고 해야 한다.

1단계

if (empty) then recommendation = "soft"

Age = young, 1/7
    = pre-presbyopic, 1/7
    = presbyopic, 0/7
    
Spectacle prescription = myope , 2/12
                       = hypermetrope, 0/9
                       
Astigmatism = no, 2/9
            = yes, 0/12
            
Tear production rate = reduced, 0/12
                     = normal, 2/9
                     
Astigmatism과 Tpr 이 같지만 이번에는 Tpr을 고르겠습니다.

2단계

if Tear production rate = normal And (empty) then recommendation = "soft"

Age = young, 1/3
    = pre-presbyopic, 1/3
    = presbyopic, 0/3
    
Spectacle prescription = myope , 2/6
                       = hypermetrope, 0/3
                       
Astigmatism = no, 2/6
            = yes, 0/3

Astigmatism과 sp가 같지만 sp를 고르겠습니다.

3단계

if Tear production rate = normal And Spectacle prescription = myope 
And (empty) then recommendation = "soft"

Age = young, 1/2
    = pre-presbyopic, 1/2
    = presbyopic, 0/2
    
Astigmatism = no, 2/3
            = yes, 0/3

Astigmatism 이 2/3으로 가장 높기에 Astigmatism 선택!

아직 perfect 하지 않기 때문에 계속 진행!

if Tear production rate = normal And Spectacle prescription = myope 
And Astigmatism = no And (empty) then recommendation = "soft"

Age = young, 1/1
    = pre-presbyopic, 1/1
    = presbyopic, 0/1

and so on
~~~

## Rules vs Trees

Tree = attribute의 정부 분류의 집중 (Class 값을 우선적으로 생각하진 않는다)

Rule = 특정 Class의 맞는 Rule을 선택한다. (Rule의 순서를 지정할 수 없다.)
