---
layout:     post
title:      "About Confusion Matrix"
subtitle:   "Confusion Matrix 개념 및 구하기"
date:       2019-09-24 20:51:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: Data_mining
tags:
  - Data mining
---

### confusion matrix

~~~
Tp Fn   9 0
      =
Fp Tn   5 0
~~~

Tp = instance에 대한 recommendation이 yes 인데 yes (True and positive)

Fn = instance에 대한 recommendation이 yes 인데 no (False and negative)

Fp = instance에 대한 recommendation이 no 인데 yes (False and positive)

Tn = instance에 대한 recommendation이 no 인데 no (True and negative)

##### 정확도(accuracy)

recommendation 이 얼마나 정확한지!

위의 confusion matrix 에서는

9/ 14 (올바른 recommendation / 전체 recommendation)

##### 정밀도(precision)

Yes에 대한 것 = 9/14 (yes의 맞는 개수/ 전체 yes의 개수)

> Tp/(Tp + Fp)

No에 대한 것 = 0/0 (no의 맞는 개수 / 전체 no의 개수)

> Tn/(Fn + Tn)

세로!!!

##### 재현율(recall)

Yes에 관한 것 = 9/9 (yes가 나와야 하는 yes의 개수 / 전체 yes가 나와야 하는 것의 개수)

> Tp /(Tp + Fn)

No에 관한 것 = 0/5 (no가 나와야 하는 no의 개수 / 전체 no가 나와야 하는 것의 개수)

> Tn/(Fp + Tn)

가로!!
