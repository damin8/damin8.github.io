---
layout: post
title: "Git Branch"
subtitle: "Git Branch 전략"
date: 2021-07-01 15:34:00
author: "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog: true
categories: ETC
tags:
  - ETC
---

## git branch management strategy

- **여러 개발자**가 협업하는 환경에서 git 저장소를 효과적으로 활용하기 위한 work-flow

- 브랜치의 생성, 삭제, 병합이 자유로운 git의 유연한 구조를 활용하여 다양한 방식으로 소스관리

```
만약 브랜치 전략이 없다면?

- 어느 브랜치 가 최신인지? -> 헷갈릴 수 있다

- Hot fix 가 필요한 상황이 있을 수 있는데, 어떤 브랜치 를 기준으로 배포를 해야하나? 배포 버전은? -> 기준이 없기에 혼돈이 온다
```

## git-flow

- 5가지의 브랜치를 이용해 운영하는 브랜치 전략

- **항상 유지**되는 2개의 main 브랜치, **역할 수행이 완료되면 사라지는** 3개의 sub 브랜치 로 구성되어 있다

### main branch : **항상 유지**

1. master : 제품으로 출시될 수 있는 브랜치

2. develop : 다음 출시 버전을 개발하는 브랜치

### sub 브랜치 : **merge 후 소멸**

1. feature : 기능을 개발하는 브랜치 (develop 브랜치 기반)

2. release : 이번 출시 버전을 준비하는 브랜치. develop 브랜치 개발이 완료되면 qa, test 실행을 위해 임시로 사용하는 브랜치

3. hotfix : 출시 버전에서 발생한 버그를 수정하는 branch (master 브랜치 기반)

### git-flow 개발 프로세스

1. 개발자는 develop 브랜치로부터 본인이 개발할 기능을 위한 feature 브랜치를 생성

2. feature 브랜치에서 기능을 만들다가, 기능이 완성되면 develop 브랜치에 merge

3. 이번 배포 버전의 기능들이 develop 브랜치에 모두 merge 됐다면, QA를 위해 release 브랜치를 생성합니다

4. release 브랜치에서 오류가 발생했다면 release 브랜치 내에서 수정. 마침내 QA가 끝났다면, 해당 버전을 배포하기 위해 master 브랜치로 merge. bugfix 가 있었다면 해당 내용을 반영하기 위해 develop 브랜치에도 merge

5. 만약 제품(master) 에서 버그가 발생한다면, hotfix 브랜치를 생성

6. hotfix 브랜치에서 버그 픽스가 끝나면, develop 과 master 브랜치에 각각 merge

## github-flow

- 제품이 release 되는 최신 버전인 master 브랜치만 존재

### github-flow 개발 프로세스

- 기능 개발, 버그 픽스, 혹은 어떠한 이유로든 브랜치 생성

`git-flow 처럼 체계적인 분류가 없기 때문에 브랜치 이름은 의도를 아주 잘 드러내도록 작성`

- 열심히 개발하면서 커밋 메시지는 상세하게 !

- Pull Request 를 생성

- Pull Request 에 대해서 충분한 review 와 토의

- 4번이 끝나면 해당 내용을 실제 서버(혹은 테스트 환경)에 배포

- 이상이 없다면 master에 merge 후 push 하고, 즉시 배포 (배포 자동화 권장)

### github-flow 특징

1. 브랜치 전략이 단순해서 git을 처음 접하는 사람들에게도 유용

2. CI(지속적 통합), CD(지속적 배포)가 자연스럽게 이루어진다

## 어떤 전략을 사용해야 하지?

1. 한달 이상의 긴 호흡으로 개발하여 주기적으로 배포하고, QA 및 배포, hot fix 등을 수행할 수 있는 여력이 있는 팀이라면 git-flow

2. 항상 릴리즈 되어야 할 필요가 있는 서비스와 지속적으로 테스트하고 배포하는 팀이라면 github-flow 와 같은 간단한 workflow 가 적합

## Reference

[웨지의 Git 브랜치 전략](https://www.youtube.com/watch?v=jeaf8OXYO1g)

<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>
