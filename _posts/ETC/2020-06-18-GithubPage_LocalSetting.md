---
layout:     post
title:      "Github 페이지 Local Setting"
subtitle:   "환경 구성 및 관리"
date:       2020-06-18 12:31:00
author:     "Damin"
header-img: "img/tag-bg.jpg"
header-mask: 0.3
catalog:    true
categories: ETC
tags:
  - ETC
---

2019년.. 부터 공부했던 것을 정리하곤 했다.

Github Page를 사용하기 전에는 Github Repository에 그저 글을 올렸지만

2020년이 되면서 Github Page를 '만들어야 겠다!' 라고 결심했다.

그러고 2월에 Github Page를 Jekyll를 통해 쉽게 만들게 됐다.

새로 Github Page를 받고 내 것으로 만들기에 엄청난 시간이 걸렸지만 기분이 좋았다.

그때는 Jekyll은 Github에서만 돌아가는줄 알았다.

계속 블로그에 글을 쓰다보니 불편한 점이 한 두가지가 아니었다.

1개 수정하면 그 수정을 보기 위해 Commit을 하게 되고, 기다리고....

Error가 나면 어디서 Error가 나는지..

이런 시간들이 엄청나게 소비가 됐다.

이제 조금씩 시간이 지나면서 이러한 시간들이 너무 아깝다고 생각이 들었고

Google Search Console에 등록하는 과정중에 굉장히 많은 스트레스를 받았다.

그래서 Local에서 환경을 구성하기로 마음 먹었다. (왜 이제야 했을까 싶다...)

잡소리는 그만하고.. 많이 했지만..

# Ruby 설치

Jekyll은 Ruby로 만들어졌다.

블로깅하는거 때문에 Ruby를 다운받는 것은 부담일 수 있다. (참고)

[https://rubyinstaller.org/downloads/](https://rubyinstaller.org/downloads/)에서 다운 받자.

> Devkit 포함 된 걸로! 중간에 PATH 추가하냐고 나오는데, 꼭 체크해주자

# Jekyll 설치

검색 -> start command prompt with Ruby

console 창에서 **gem install jekyll bundler** 입력!

마구마구 다운 받는다~~!

![1](/img/in-post/ETC/JekyllDownload.PNG)<br>

다운 다 됐으면 **jekyll -v** 로 확인! (버전 확인)

![1](/img/in-post/ETC/JekyllVersion.PNG)<br>

# Github Page 연동

이제 Github Page 연동할 차례다.

필자는 Editor로 Atom과 Visual Code를 고민하다 Visual Code를 선택했다!

물론, 제비뽑기로 뽑은 것이 아닌 나름대로 이유가 다 있었다.

[Visual Code 다운로드](https://code.visualstudio.com/download)

자신의 OS에 맞게 다운로드!

Visual Code를 실행시켜서 Local에 있는 github.io 디렉터리를 연다! (Open Folder)

Visual Code에서 **ctrl + j**를 이용해 Terminal을 킨 후

**jekyll serve** 명령어를 입력!

> stack trace를 보기 위해서는 **jekyll serve --trace**

그럼 실행이 되는 것을 확인 할 수 있다.

![1](/img/in-post/ETC/VisualCodeJekyll.PNG)<br>

Default port 는 4000번이다.

# Local 환경 세팅 후 느낀점

확실히 편하다...

기존에 에러 때문에 시간 버린 것 + 수정이 잘 됐나 확인 하는 시간 및 고통 및 비효율적인 commit

너무나도 미리 했어야 하는데 미리 안한것이 후회가 된다.

이제부터라도 스트레스를 덜 받자!

<script src="https://utteranc.es/client.js" repo="damin8/blog-comment" issue-term="title" label="Comment" theme="github-light" crossorigin="anonymous" async>
</script>






