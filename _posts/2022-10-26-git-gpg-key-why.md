---
title: Git GPG key 사용할까?
author: keumbi
date: 2022-10-26 10:20:00 +0900
categories: [Error Handling Log]
tags: [git, gpg key, error, intellij]
---

![Window shadow](https://media0.giphy.com/media/CoND5j6Bn1QZUgm1xX/giphy.gif){: .shadow style="max-width: 60%" }

## Overview
의식에 흐름 없이 맥북 업데이트를 하고, 과제를 제출하려는 순간... 두둥!! 인텔리제이에서 에러 발생!! 커밋이 안 됐다. 급히 터미널을 열고, 다시 시도했지만, 같은 에러 메시지를 토해냈다. `error: gpg failed to sign the data` 이 에러는요... 레퍼런스에 있는 링크를 참조해서 한 땀 한 땀 적용해 봅니다.

## GitHub Keybase
<div class="iframe-container"><iframe src="https://www.youtube.com/embed/4V-7KnhcrbY" title="YouTube video player" frameborder="0" allowfullscreen></iframe></div>
_4년전 영상이지만 참고하기 좋습니다._

## Conclusion

```
git config --global  commit.gpgsign false
```
그냥 사용 안 할 거야... 하면 되는 거였다!!

### Conclusion + 자매품 :wink:
```
git config --global http.sslVerify false
```



## Reference
<https://github.com/pstadler/keybase-gpg-github#optional-in-case-youre-prompted-to-enter-the-password-every-time>

<https://stealthpuppy.com/signing-git-commits-for-sweet-verified-badges/>

<https://director-joe.kr/74>

<https://www.jetbrains.com/help/idea/2022.2/set-up-GPG-commit-signing.html#add-gpg-key-to-your-account>

<https://xmlangel.github.io/Gpg/>

<https://zetawiki.com/wiki/RPM-GPG-KEY_%ED%8C%8C%EC%9D%BC_%EB%A7%8C%EB%93%A4%EA%B8%B0>

<https://choco0908.github.io/docs/etc/3/>

<https://johngrib.github.io/wiki/gpg/>
