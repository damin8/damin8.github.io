---
layout:     post
title:      "Symmetric Key"
subtitle:   "A5/1 & RC4"
date:       2019-08-30 21:31:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: System_Security
tags:
  - System_Security
---

## Symmetric Key Crypto

### Stream Ciphers

대칭 키 암호의 구조 중 하나이다.

유사난수를 연속적으로 생성, 암호화 하려는 자료와 결합

일반적인 스트림 암호는 유사난수를 1비트 단위로 생성

암호화하려는 각 값을 xor하여 1비트의 암호화된 자료를 얻는다

one -time pad 랑 방식이 비슷하다.

- KeyStream 을 어떻게 구성하냐가 문제!

Sender 와 receiver 둘 다 같은 Stream Cipher algorithm을 가지고 있고, 둘 다 Key k를 알고 있다!

키의 길이가 

#### A5/1

- shift register의 기반을 둔다

- GSM mobile phone system 에서 사용되곤 한다

3개의 shift register를 가지고 있다고 가정하자

X : 19 bits

Y : 22 bits

Z : 23 bits

A5/1 은 총 64bit를 가지고 있다(19 + 22 + 23 = 64)

매 step에서 특정한 인덱스(ex. X8, Y10, Z10)에서 0과 1중에 더 많은 것을 고른다. (이 인덱스들을 Clocking bit라고도 한다)

> M = maj(0,1,1) = 1, M = maj(0,0,1) = 0

이렇게 M을 구한 후에 각 shift register에 맞는 알고리즘을 돌린다.

그렇게 해서 얻은 shift register의 마지막 bit들을 xor 연산을 취한 후에 KeyStream을 얻는다.

#### RC4

- A5/1는 Bit 단위지만, RC4는 byte 단위 이다.

- 자기가 수정하는 Lookup table의 기반을 두고 있다

- 다양한 분야에서 이용되고 있다

- 테이블은 항상 0,1,....255의 어떤 순열을 포함한다

- 키를 이용하여 순열을 초기화 시킨다

- 각 단계에서 현재 Lookup table 요소들을 교환 -> 테이블에서 키스트림 바이트를 선정

- 각 단계는 byte를 생성 (소프트웨어에서 효율적이다)

- 단순하다! (table은 항상 0~255의 순열을 가지고 있기 때문에!)

- S[] 는 0~255의 순열

- key[]는 key의 N 바이트를 함유한다

1 단계 (Reset)

~~~

for i = 0 to 255
 
  S[i] = i
  K[i] = key[i(mod N)]
  
next i

~~~

2 단계 (Shuffle)

~~~ 

j = 0

for i = 0 to 255

    j = (j + S[i] + K[i]) mod 256
    swap(S[i],S[j])
    
next i

i = j = 0

~~~

3 단계 (Make KeyStream)

~~~

i = (i + 1) mod 256
j = (j + S[i]) mod 256
swap(S[i],S[j])
t = (S[i] + S[j]) mod 256
KeyStreamByte = S[t]

~~~

- 처음 256 byte 는 무조건 폐기 되어야 한다 (like one-time pad)

##### 정리

Stream Ciphers는 하드웨어 효율적이지만, 소프트웨어에는 구축하기에 어려움이 있다고 합니다.

과거에는 매우 인기가 많았지만 현재는 프로세스들이 매우 빠르기 때문에 Software 기반의 crypto 를 많이 사용합니다.
