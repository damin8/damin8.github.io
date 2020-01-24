---
layout:     post
title:      "Symmetric key -2"
subtitle:   "Block Cipher"
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

## Block Cipher

- plaintext and ciphertext 는 고정된 길이의 블록으로 이루어져 있다

- 목표 : 안전성, 효율성

- 안전성과 효율성 둘다 지키기 어렵다

> 효율성을 높이면 안전성이 떨어지고, 안전성이 높아지면 효율성이 낮아진다

- 블록들로 output(ciphertext or plaintext)이 나온다

![roundfunction](/img/in-post/SystemSecurity/roundfunction.PNG) <br>

F = round function

K = subkey

**Encryption**

각 라운드가 끝나면 그 라운드의 cipherblock이 나오고

그 cipherblock으로 다시 Round Function 을 다시 실행한다.

> 전 라운드의 output = 이번 라운드의 input

이렇게 n번을 반복하면 ciphertext가 나온다!

**Decryption**

ciphertext를 Encryption 과 동일한 방법으로 Decryption을 해준다.

### Feistel Cipher

- 입력되는 plaintext block을 left, right 으로 나눈다

- Des : 한 블록의 크기 = 64bit

- Des : 16번의 라운드

#### Encryption

![feistel](/img/in-post/SystemSecurity/feistel.PNG) <br>

1 round output = L1 R1

2 round = L2 R2

.
.
.

n round = Ln Rn

Ln + Rn = ciphertext

이 형태를 feistel cipher를 따른다고 한다.

#### Decryption

![feistelde](/img/in-post/SystemSecurity/feistelde.PNG) <br>

- Encrytion의 식으로 Decryption 식을 유추할 수 있다.

- F(R(i-1),Ki) = 0 이 될 수도 있다.

이렇게 된다면, Ri xor 0 = Ri 이다.

식에 따라서

R(i-1) = Li

L(i-1) = Ri

그저 둘이 바꾼게 된다.

Round가 짝수번이면 원래 평문이 나오게 되고

Round가 홀수번이면 left 와 right 를 바꾼게 된다.

**안전상의 문제!!!**

따라서 Function을 잘 짜야 한다.

> 잘 짜여진 Function에 대해서만 secure하다.

#### DES

- 64 bit block length

- 56 bit key length

- 16 rounds

- 매 라운드에 48 bit 의 key 가 사용된다(subkey)

- DES 방식은 expend S-boxes P Box 를 사용한다.

- S-box = 6비트를 4비트로 map 시킨다.

> 48 bit 가 들어오면 32 bit로 out (8개의 S-boxes)

#### 한 라운드의 des

![des](/img/in-post/SystemSecurity/des.PNG) <br>

#### expand

![expand](/img/in-post/SystemSecurity/expand.PNG) <br>

- 각 섹션에서는 1~4bit = 2~5bit 로 복사

- 복사된 bit의 첫번째 부분은 그 전 섹션의 4번째 bit

- 복사된 bit의 마지막 부분은 다음 섹션의 첫번째 bit

#### S-box

![S-box](/img/in-post/SystemSecurity/S-box.PNG) <br>

bit의 0,5 index = 행

bit 1,2,3,4 index = 열

ex) 0 1 1 0 1 1 -> 0 1 (0,5 index) = 1행, 1 1 0 1 (1,2,3,4 index) = 13열

#### DES subkey

- 56 bit

- 0~55의 수를 가진다

- left right 로 나눈다

#### Last word

- Round 1 전에 초기화를 한번 해준다

- 마지막 round 에서 swap

#### Security of DES

- DES의 security 는 s-box에 중점을 두고 있다

- 다른 것들은 linear한 성격을 가진다
