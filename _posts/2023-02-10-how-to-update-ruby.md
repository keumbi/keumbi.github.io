---
title: Ruby Update
author: keumbi
date: 2023-02-10 21:20:00 +0900
categories: [How to...]
tags: [update, ruby, mac]
---

## Overview

블로그 배포가 계속 실패하고 있다. ㅠㅠ 해결을 위해 루비를 업데이트 해보기로 했다.

맥을 사용하고 있고 루비를 업데이트 하기 위해 아래 코드를 한 줄씩 차례대로 실행했다.

```shell
brew update

brew install rbenv

rbenv install 3.1.2
```

위에 처럼 버전을 직접 입력해도 되고 `rbenv install -l`를 입력하면 업데이트 가능한 버전 리스트을 알 수 있다.


## Mac에서 Ruby 버전 확인

Ruby Update 업데이트가 되었는지 아래 명령어로 확인합니다.

```shell
ruby -v
```

만약, 아직도 이전 버전을 반환할 경우

## Mac Ruby update 오류

rbenv 버전 확인

```shell
rbenv versions

2.7.5
2.7.7
* 3.1.2 (set by /Users/uername/.rbenv/version)

```
터미널에 설치된 버전들이 위에 처럼 출력된다.

```shell
rbenv global 3.1.2
```
자신이 설치한 버전을 입력하여 System에서 3.1.2 버전으로 변경합니다.

다시 버전을 확인 후 제대로 버전이 변경됐다면, 환경 변수를 설정합니다.

## 환경 변수 설정

vim ~/.zshrc로 zshrc 파일 열기

zshrc 파일 맨 끝에 `eval "$(rbenv init - zsh)"` 붙여 넣기

```shell
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init - zsh)"
```

버전 적용됐는지 확인

`ruby -v`

정상적으로 Ruby 버전 업데이트와 적용이 모두 완료되었습니다.

## Reference

[Ruby rbenv 설치](https://developak.tistory.com/entry/Ruby-%EB%A3%A8%EB%B9%84-rbenv-%EC%84%A4%EC%B9%98)
