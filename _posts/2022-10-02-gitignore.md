---
title: gitignore는 무엇인가?
author: keumbi
date: 2022-10-02 21:20:00 +0900
categories: [How to...]
tags: [github pages, error, gitignore, git ignore]
---

## Overview

열심히 올렸던 깃허브 파일에서 사실 올리면 안될 파일이 올려졌다는 것을 알게되었다. .gitignore가 어떤 일을 하는 파일 인지, 이미 올린 파일들을 삭제하는 방법은 무엇인지 알아보려고 한다.

## 1. .gitignore?

Git 버전 관리 사용시 제외할 파일 목록을 지정해 주는 파일이다. 프로젝트 생성시 자동으로 생성되는 로그파일이나 빌드할 때 생기는 파일 예를 들어 class 파일 등 이런 파일들을 git이 트렉킹하지 않토록 알려주는 파일이 .gitignore이다.

## 2. .gitignore 설정하기

.git 파일이 있는 최상위 디렉터리로 이동한다.

터미널에서 아래 명령어를 이용해 .gitignore 파일을 만든다.

```shell
// .gitignore 파일을 생성한다.
touch .gitignore
// .gitignore은 숨김 파일이므로 아래의 2가지 방법으로 제대로 생성됐는지를 확인한다.
la
ls -a
// .gitignore 파일을 수정한다.
vi .gitignore
```
.gitignore 파일은 꼭 터미널에서 만들 필요 없이 자신이 사용하는 에디터로, .git 파일이 존재하는 곳과 같은 디렉터리에 만들어 주면 된다.

GitHub에서 거의 모든 언어에 대한 .gitignore 파일을 미리 만들어서 제공하고 있다. [github/gitignore](https://github.com/github/gitignore)를 참고하여 .gitignore 안의 내용을 채우면 된다.

직접 .gitignore 파일을 설정하고 싶다면 [온라인에서 직접 설정해서 만들어주는 사이트로 이동](https://www.toptal.com/developers/gitignore)해서 만들어 사용하면 된다.


## 3. Github에 잘못 올린 파일 삭제

.gitignore 설정하지 않은 상태에서 git remote(GitHub)로 push 하였을 경우 삭제하는 방법
```shell
// (1) 파일 삭제 git rm --cached r [some-directory]
$ git rm -r --cached FolderName

// (2) 파일을 원격 저장소에 올리기
git commit -m "Removed folder from repository"

// (3) 원격 저장소(origin)에 push
$ git push origin main

```

### 3.1. rm 도움말

터미널에서 `git rm -r --help` 입력하면 아래 내용을 확인 할 수 있다.
```shell
git rm -r --help
usage: git rm [<options>] [--] <file>...

    -n, --dry-run         dry run
    -q, --quiet           do not list removed files
    --cached              only remove from the index
    -f, --force           override the up-to-date check
    -r                    allow recursive removal
    --ignore-unmatch      exit with a zero status even if nothing matched
    --sparse              allow updating entries outside of the sparse-checkout cone
    --pathspec-from-file <file>
                          read pathspec from file
    --pathspec-file-nul   with --pathspec-from-file, pathspec elements are separated with NUL character
```




## Reference
[Git Remote로 잘못 push 된 디렉토리 삭제하기](https://mobicon.tistory.com/266)

[Remove directory from remote repository after adding them to .gitignore](https://stackoverflow.com/questions/7927230/remove-directory-from-remote-repository-after-adding-them-to-gitignore)
