---
title: Section1, Week3, Day 7 TIL
author: keumbi
date: 2022-08-29 21:20:00 +0900
categories: [Look back, Day]
tags: [week3, git]
published: false
---

## Daily to-do list

- [x]  Z. 굿모닝세션
- [x]  C. 버전관리 시스템 Git
- [x]  C. Git Workflow
- [x]  L.
- [x]  P. Simple Git Workflow
- [x]  S. Git Command Checkpoint
- [x]  Z.
- [x]  S. Pari Review & Unit Review

## 계획 단계
학습을 시작하기전 나의 현재 상태를 모니터링 해 봅시다.
아래 두 가지 질문에 대한 답을 천천히 생각해 본 후, 개인 블로그나 노트를 활용하여 기록합니다.

✅ **오늘 나의 학습 목표는 무엇인가요?**
- Git 기초
  - Git의 환경설정을 할 수 있다.
  - 버전 관리 시스템의 필요성을 이해할 수 있다.
  - Github과 Git의 관계에 대해 이해할 수 있다.
  - Repository에 대해 이해할 수 있다.
    - Local Repository와 Remote Repository의 차이를 이해할 수 있다
- 버전 관리 시스템 -Git
  - Git의 탄생 배경과 Git이 제공하는 유용한 기능을 이해함으로써, Git이 무엇인지 이해한다.
  - Git과 Github의 차이를 설명할 수 있다.
- Git 설치
  - Git을 설치하고, 환경 설정을 할 수 있다.
  - SSH 키를 생성하여 Github에 등록할 수 있다.
- Git Workflow
  - 혼자 작업하는 경우의 workflow를 이해한다.
  - 함께 작업하는 경우의 workflow를 이해한다.
  - 상황에 따라 Github의 기능과 Git 명령어를 사용할 수 있다.
    - Fork
    - clone
    - status
    - restore
    - add
    - commit
    - reset
    - log
    - pull
    - push
    - init
    - remote add
    - remote -v
  - Git의 세 가지 영역 및 상태를 이해한다. (Committed, modified, staged)
  - Remote Repository를 페어와 공유하며 협업을 할 수 있다.
  - 충돌이 발생했을 경우 해결할 수 있다.
  - Advanced Challenge
    - Git Repository의 commit되지 않은 변경 사항을 취소할 수 있다.
      - `reset HEAD <file>`
      - `checkout -- <file>`
    - 협업을 위한 git 개념을 이해할 수 있다.
      - branch, merge의 개념
      - remote repository에서 origin과 upstream의 차이점

✅ **오늘 학습할 내용 중에 이미 알고 있는 내용은 무엇인가요?** Git 이 무엇이고, 언제 사용하는지(개념)


## Overview

실행 중인 텍스트 에디터에서는 Ctrl + z를 여러 번 눌러 이전 상태로 돌아갈 수 있지만, 코드를 수정한 뒤 에디터를 종료했다면, 다시 실행한 텍스트 에디터에서 이전 코드로 돌아갈 수 없습니다. 이런 경우를 위해서라도 이전에 작성한 내용을 보존해야 할 필요가 있습니다. 다행히 이전에 작성한 내용을 보존해 주는 시스템이 있습니다. 이 시스템이 바로, 버전 관리 시스템(Version Control System)입니다.


## 1. 버전관리시스템 Git

Git- 파일 관리 프로그램 (버전 관리, 백업, 협업)

버전 관리: Git 관리하는 디렉토리(폴더)에 어떤 문서를 만들면 Git으로 그 문서의 버전을 관리할 수 있음

백업하기: 온라인 원격 저장소에 백업할 수 있음

협업하기: 여러 작업자가 하나의 작업물의 다른 부분을 각자 작업할 때, 작업물을 공유하고 취합할 수 있게 도와줌

[https://www.youtube.com/watch?v=2ReR1YJrNOM](https://www.youtube.com/watch?v=2ReR1YJrNOM)

Github: Git Repository를 관리할 수 있는 클라우드 기반 서비스 , Git이 설치되어 있는 클라우드 저장소

**버전 관리를 사용하는 이유**

1. 파일이 변경되면 변경 이력을 저장할 수 있다.
2. 이전 버전으로 돌아갈 수 있다.
3. 어떤 변경 사항이 발행했는지 알아보기 쉽다.
4. 협업 하기 좋다.
5. 백업용

Git 장점: 소스 코드 변경 이력 쉽게 확인 가능, 특정 시점에 저장된 버전과 비교 가능, 특정 시점으로 되돌아갈 수 있음

**Git은 로컬에서 버전 관리해주는 프로그램, Github은 Git을 클라우드 방식으로 구현한 서비스**
![git pull request](https://image.slidesharecdn.com/githubpull-request-150905094316-lva1-app6892/75/github-how-to-pull-request-1-2048.jpg){: .shadow style="max-width: 90%" }

출처: designless.net

- `add`, `commit`, `push` : 온라인 원격 저장소에 업로드
- `fork`, `clone` : 협업자의 작업물을 나의 로컬에 다운로드
- `pull request` : 상대 협업자에게 나의 작업 완성물을 취합해달라고 요청
- `merge` : 상대방의 작업물과 나의 작업물을 취합

**Git Repository:** 저장소, 파일이나 폴더를 저장해두는 곳, git으로 관리되는 폴더를 말함

**Remote Repository:** 원격 온라인 서버 상의 저장소 (여러 사람이 함께 공유 가능)

**Local Repository:** 내 컴퓨터의 저장소 (개인 전용 저장소)

**스냅샷:** 특정 시점에 생성된 백업 복사본

**commit:** 하나하나 스냅샷을 만들어 주는 작업

**Fork:** 프로젝트에 contribute 하기 위해 원격 저장소(Remote Repository)를 내 원격 저장소로 가지고 오는 작업

**Clone:** 원격 저장소(Remote Repository)에 있는 코드를 내 컴퓨터로 가져 오는 것

**Push:** 변경된 내용을 commit을 통해 저장해준 뒤, 원격 저장소(Remote Repository)에 올려주는 작업

**Pull request:** 내가 제안한 코드 변경 사항 반영 여부 요청

**Pull:** 원격 저장소(Remote Repository)에 변경 사항이 있을 때 개인 전용 저장소(Local Repository)로 가져오는 작업


## 2. Git 설치

Git 설치- git for windows 검색 & 설치

[Git 최초 설정](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95)

SSH 키 생성

공개키 복사

공개키 등록

## 3. Git Workflow

1. Remote에 있는 다른 Repository에서 Fork를 해서 Remote에 있는 내 Repository에 가지고 옵니다.
2. 그리고 이 코드를 수정하기 위해서는 내 컴퓨터로 가져오는 작업이 또 필요합니다. 내 컴퓨터에서 작업을 하기 위해서 clone을 합니다.
3. 이제 내 컴퓨터의 작업 공간 (work space) 에서 작업에 들어간 파일들을 git의 관리하에 있는 상태로 올려줄 수 있습니다. 이 영역을 staging area라고 말합니다. 즉, staging area에 들어오지 않은 파일은 unstaged 혹은 untracked file이라고 말하며, staging area에 있는 파일들은 staged 된 파일이라고 말할 수 있어요. 이 부분에 대해서는 나중에 더 자세하게 알아봅시다.

4. staging area에 들어온 파일들은 commit이 가능합니다. commit을 하고 나면 내 remote repository에 push 해서 commit 기록을 remote 에도 남겨줄 수 있습니다.

5. push를 완료한 후 이제 remote의 원래 레파지토리에 pull request를 보내면 Remote Repository로 내가 수정한 코드를 업로드할 수 있습니다.

이 그림이 이번 강의의 전체적인 그림이기 때문에 지금은 이런 순서대로 진행이 된다는 것만 알아두시면 workflow를 이해하기 수월하실 거예요.
강의를 다 듣고 다시 한번 이 그림을 살펴보며 복습해 보세요!


# **Basic**

# **HELP**

**$ git 명령어 --help**

명령어에 대한 설명을 자세히 볼 수 있다.

# **기본설정**

**$ git config**

git의 기본설정을 변경할 수 있다.

**git config --global user.name "이름"**

**git config --global user.email "이메일주소"**

각각의 버전은 누가 만든것인지 정보를 가지고 있어야하는데 위와 같이 username과 email을 설정할 수 있다. (`railsinstaller`설치 후 처음 입력한 정보!)

# **새로운 저장소 만들기**

모든것은 **init**으로 부터 시작된다.

**$ git init**

**Initialized empty Git repository in /Users/dh0023/gittest/.git/**

****

**$ ls -al**

**total 0**

**drwxr-xr-x   3 dh0023  staff   102  3 23 17:08 .**

**drwxr-xr-x+ 34 dh0023  staff  1156  3 23 17:08 ..**

**drwxr-xr-x  10 dh0023  staff   340  3 23 17:08 .git**

`git init`을 하면 현재 디렉토리가 **버전관리의 저장소**가 되었다는 의미이다.

`ls -al`을 하면 `.git` directory(폴더)가 생긴 것을 볼 수 있다.`.git` 폴더 안에서 버전관리가 이루어진다.

# **상태확인하기**

**$ git status**

**On branch master**

****

**Initial commit**

****

**Untracked files:**

**(use "git add <file>..." to include in what will be committed)**

****

**test1.html**

- -------------------------

****

**Changes to be committed:**

**(use "git rm --cached <file>..." to unstage)**

****

**new file:   test1.html**

**untracked files:**은 버전관리가 되지않고 있는 파일로서 새로 추가, 수정, 삭제 즉 변경된 파일이다. 버전관리가 되지않고 있는 파일,폴더는 **붉은색**으로 표시 된다.

**new file:**은 버전관리에 새로 추가된 파일이며, **초록색**으로 표시된다.(`git add`명령어를 통해 추가)

# **추가**

**$ git add 파일(폴더)명**

**$ git add test1.html**

****

**$ git add .**

버전관리 목록에 추가해 주는 것이다.

`git add .`은 변경된 모든 사항을 추가한다는 의미

`add`명령어 후 `git status`를 해보면 **changed to be Committed:** 파일이 버전관리 되고 있는 것을 확인 할 수 있다.

# **확정**

**$ git commit -m "first commit"**

**[master (root-commit) dc423a2] first commit**

**1 file changed, 1 insertion(+)**

**create mode 100644 test1.html**

이때까지 변경된 것을 **확정**하는 것이다. `""`안에는 버전에 대한 설명을 간단히 적어준다.

**$ git commit --amend**

**[master c6ce442] first commit**

**Date: Thu Mar 23 17:28:55 2017 +0900**

**1 file changed, 1 insertion(+)**

**create mode 100644 test1.html**

**추가적인 설명**을 자세하게 적을 수 있다.

![https://3827551924-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M26jG1uJ-xuMP0XPOri%2F-M28eYY8Gfew1RKJ2YsW%2F-M28e_H5I1HEWQwMbomv%2F735.png?generation=1583931351997064&alt=media](https://3827551924-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M26jG1uJ-xuMP0XPOri%2F-M28eYY8Gfew1RKJ2YsW%2F-M28e_H5I1HEWQwMbomv%2F735.png?generation=1583931351997064&alt=media)

# **서버에 올리기**

현재의 변경 내용은 아직 로컬 저장소의 HEAD 안에 머물고 있다. push명령어 이후에 변경내용이 서버에 적용된다.

`git push [리모트 저장소 이름] [브랜치 이름]`

master 브랜치를 origin 서버에 올리려면 아래와 같이 하면된다.

**$ git push origin master**

# **저장소 받아오기**

**$ git clone /로컬/저장소/경로**

특정 브랜치로 저장소를 받아오고 싶으면 아래와 같이 옵션을 주면 된다.

**$ git clone -b {branch_name} --single-branch {repository_url}**

# **취소**

**$ git reset [돌아갈 버전]**

**$ git reset HEAD~1**

Reset은 **선택한 버전의 상태로 돌아가는 것, 버전을 지워버림**

![https://3827551924-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M26jG1uJ-xuMP0XPOri%2Fsync%2F6d37465b87c360e7b674a55dd5a2e23bb2a3dcbf.png](https://3827551924-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M26jG1uJ-xuMP0XPOri%2Fsync%2F6d37465b87c360e7b674a55dd5a2e23bb2a3dcbf.png)

https://res.cloudinary.com/practicaldev/image/fetch/s--vtdH0y_D--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/f0ae16e339631560090233b4c5850990/git-reset.png

**$ git revert [돌아갈 버전]**

**$ git revert HEAD ~1**

Revert는 **선택한 버전을 취소해서 그 이전 상태로 돌리는것**

![https://3827551924-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M26jG1uJ-xuMP0XPOri%2F-M28eYY8Gfew1RKJ2YsW%2F-M28e_H9XSdNw2UGT4ar%2Fgit-revert.png](https://3827551924-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M26jG1uJ-xuMP0XPOri%2F-M28eYY8Gfew1RKJ2YsW%2F-M28e_H9XSdNw2UGT4ar%2Fgit-revert.png)

https://res.cloudinary.com/practicaldev/image/fetch/s--jatxl5-W--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://storage.kraken.io/kk8yWPxzXVfBD3654oMN/782bf25d88e360df15ef96d84d872181/git-revert.png

`revert` 와 `reverse` 를 할때는 항상 주의해야한다.

# **Branch 생성하기**

branch는 안전하게 격리된 상태에서 무언가를 만들 때 사용.

**$ git branch**

- master

저장소를 새로 만들면 **master** branch(default)가 기본이다.

**$ git branch <브랜치명>**

**$ git branch exp**

**$ git branch**

**exp**

- master

실험적인 작업을 해야하는경우나 **협업**을 할 때 사용. exp branch가 생성된 것을 확인할 수 있다. *붙은 것이 현재 branch

이전 commit으로 branch를 생성

**$ git branch <브랜치명> [특정 버전]**

**$ git branch example 9da3066404c68a4e7f77a7ddb69beb4d2475e2dd**

해당 commit에서 브랜치가 생성된다.

[git log에 대해 알아보기](https://dahye-jeong.gitbook.io/til/git/2019-01-09-git-log)

# **현재 Branch변경**

**$ git checkout exp**

- exp

**master**

현재 branch가 *exp로 바뀐것을 확인 할 수 있다.

**$ git checkout -t origin/exp**

remote에 있는 branch를 가져와 로컬에 동일한 이름의 브랜치를 생성하면서 해당 branch로 checkout하는 옵션이다.

**$ git branch**

- exp

**master**

# **Branch 생성과 동시에 변경하기**

**$ git checkout -b <브랜치명>**

**$ git checkout -b example1**

**$ git branch**

- example1

**master**

# **데이터 가져오기(fetch)**

fetch는 단순히 원격 저장소의 내용을 확인만 하고 로컬 데이터와 병합은 하고 싶지 않은 경우에 사용한다.

**$ git fetch [remote-name]**

즉, local에는 없지만 remote 저장소에 있는 모든 데이터를 가져온다.

# **Branch 병합**

**$ git merge <branch명>**

branch를 이용해 병합을 하면 git이 자동으로 commit을 해준다.

**$ git branch**

**example1**

- master

****

**$ git merge example1**

# **Merge --squash**

병합할 branch의 모든 commit을 하나로 합치고 싶을때 `--squash` 옵션을 지정하면된다.

**$ git merge --squash <branch명>**

**$ git merge --squash example1**

# **갱신(pull)**

**$ git pull**

원격 저장소의 변경 내용이 로컬 작업 디렉토리에 받아지고(fetch), 병합(merge)된다.

# **충돌(conflict)**

만약에 여러개의 branch가 서로 같은 것을 수정할 경우에 깃은 충돌을 나타내고 우리가 수정할 수 있도록 표시해준다.

# **협업**

어떠한 작업을 하기전에 pull을 하는 것이 가장 좋다! **`pull`->working->`commit`->`pull`->`push`**

# **stash**

아직 commit하지 않은 버전을 임시로 저장하는 것! stash를 하면 임시로 저장된 후 마지막 버전상태로 돌아가고 삭제된다.

# **tag(github에선 releases)**

설명해주는 것! 과거의 특정한 버전에 대해서도 태그를 붙일 수 있다.

# **ignore**

`.gitignore`파일에 파일을 추가하면 git이 없는걸로 간주할 대상이 된다.(github에 올릴때도 안올라감!) [ignore에 포함되어야할 목록](https://www.gitignore.io/)

이 때 중요한 id, 비밀번호, key값이 설정된 파일은 따로 저장한 후 `.gitignore`에 추가해 원격저장소에 올리지 않는다.


## 🔥 데일리 회고 - 점검 및 평가

  아래 두 가지 질문에 대한 답을 천천히 생각해 본 후, 개인 블로그나 노트를 활용하여 기록합니다.정규학습시간을 마친 후에는 정규학습시간 전에 개인 블로그나 노트에 적어둔 계획 단계에 대한 답변과, 아래 질문에 대한 답변을 블로그나 노트에 추가로 작성해 봅니다.

✅ **오늘 학습 내용 중 새롭게 배운 내용은 무엇인가요?**

git, github

✅ **오늘 새롭게 학습한 내용을 다른 사람에게 설명할 수 있나요?**

글쎄요..

✅ **오늘 학습한 내용 중 아직 이해되지 않은 불확실한 내용은 무엇인가요?**

충돌했을때 과정

✅ **이해되지 않은, 불확실한 내용을 보완하기 위해서 나는 무엇을 할 수 있을까요?**

페어와 함께했지만 주말에 다시 해보기로 함

✅ **나의 오늘 학습 만족도는 몇점인가요?** 🌑🌘🌗🌖🌕  **→**  🌖
