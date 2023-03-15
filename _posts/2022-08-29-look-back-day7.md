---
title: Section1, Week3, Day 7 TIL
author: keumbi
date: 2022-08-29 21:20:00 +0900
categories: [Look back, Day]
tags: [week3, git]
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

**Git:** 파일 관리 프로그램 (버전 관리, 백업, 협업)

- 버전 관리: Git 관리하는 디렉토리(폴더)에 어떤 문서를 만들면 Git으로 그 문서의 버전을 관리할 수 있음
- 백업하기: 온라인 원격 저장소에 백업할 수 있음
- 협업하기: 여러 작업자가 하나의 작업물의 다른 부분을 각자 작업할 때, 작업물을 공유하고 취합할 수 있게 도와줌

[https://www.youtube.com/watch?v=2ReR1YJrNOM](https://www.youtube.com/watch?v=2ReR1YJrNOM)

**Github:** Git Repository를 관리할 수 있는 클라우드 기반 서비스 , Git이 설치되어 있는 클라우드 저장소

**버전 관리를 사용하는 이유**

1. 파일이 변경되면 변경 이력을 저장할 수 있다.
2. 이전 버전으로 돌아갈 수 있다.
3. 어떤 변경 사항이 발행했는지 알아보기 쉽다.
4. 협업 하기 좋다.
5. 백업용

Git의 주요 기능 소스 코드 변경 이력 쉽게 확인 가능, 특정 시점에 저장된 버전과 비교 가능, 특정 시점으로 되돌아갈 수 있음

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

**Commit:** 하나하나 스냅샷을 만들어 주는 작업

**Fork:** 프로젝트에 contribute 하기 위해 원격 저장소(Remote Repository)를 내 원격 저장소로 가지고 오는 작업

**Clone:** 원격 저장소(Remote Repository)에 있는 코드를 내 컴퓨터로 가져 오는 것

**Push:** 변경된 내용을 commit을 통해 저장해준 뒤, 원격 저장소(Remote Repository)에 올려주는 작업

**Pull request:** 내가 제안한 코드 변경 사항 반영 여부 요청

**Pull:** 원격 저장소(Remote Repository)에 변경 사항이 있을 때 개인 전용 저장소(Local Repository)로 가져오는 작업


## 2. Git 설치

Git 설치: git for windows or mac 검색 & 설치


### 2.1. Git 환경 설정

**사용자 정보**

Git을 설치하면 가장 먼저, 사용자 이름과 이메일 주소를 설정합니다. 설정에 기록된 사용자 이름과 메일 주소를 앞으로 진행할 Git 커밋 내역에 기록합니다.

터미널 화면에 다음과 같이 입력하세요.
```shell
git config --global user.name "username" # 사용자 이름
git config --global user.email "user@email.com" # 내 이메일 주소
```
-global 옵션으로 설정하면, 사용자 홈에 저장되므로 git을 설정할 때 처음에 단 한 번만 입력해도 됩니다. 나중에 github의 사용자 이름이나 이메일을 변경한다면, 이 명령어를 다시 입력해야 합니다.

만약 여러 프로젝트를 진행하고 있어서, 프로젝트마다 다른 사용자 이름과 이메일 주소를 사용하고 싶으면 -global 옵션을 빼고 명령을 실행할 수 있습니다.

**에디터**

Git에서 커밋 메시지를 기록할 때, 특히 merge commit 확인 메시지가 나올 때 텍스트 에디터가 열립니다. 기본값으로 텍스트 에디터 vi가 열리는데, vi 에 익숙하지 않다면, nano로 변경 가능합니다.
```shell
git config --global core.editor nano
```
### 2.2. SSH 등록

**SSH 키 생성** : ssh 키는 비대칭키로 구성되며, 두 개의 키가 서로 대칭이 되지 않는 형태로 존재합니다. 다음의 명령어  `ssh-keygen`를 프롬프트에 입력하고, ssh 키 페어(쌍)을 생성하세요. 명령어를 입력 후 Enter 키를 몇 번 입력하면, ssh 키 페어가 생성됩니다.

**공개키 복사** : 다음의 명령어`cat ~/.ssh/id_rsa.pub`를 프롬프트에 입력하여, 공개키를 복사합니다.

- 마우스 우클릭 -> 복사(copy)
- Linux: Ctrl + Shift + C
- macOS: Command + C


**Github에 공개키 등록**

1. 브라우저에서 Github로 이동하여 로그인합니다. 우측 상단의 프로필 이미지를 클릭하고, Settings 에 진입
2. 왼쪽의 내비게이션에서 `SSH and GPG keys` 선택
3. 나타난 화면에서 SSH Keys 옆의 초록색 버튼 `New SSH Key` 클릭
4. 등록한 SSH 공개키를 구분할 수 있도록 사용자 임의로 Title을 작성, Key에는 복사해둔 공개키를 붙여 넣고, Add SSH Key 버튼을 클릭
5. Confirm access에서 Github 로그인에 필요한 비밀번호를 입력해 SSH key 등록을 승인

## 3. Git Workflow

### 3.1 Git의 영역과 기본 명령어

- 온라인 : Remote repository(원격 저장소)
- 로컬 : Work space(작업 공간), Staging area(스테이징 영역), Local repository(지역 저장소)


Git으로 파일 관리를 시작하기(Git 초기화) : `git init`

**.git 디렉토리** : `ls -al`

git init을 입력하면 디렉토리 내에 .git 디렉토리가 생성됩니다. 디렉토리나 파일 이름의 맨 앞에 .이 붙으면 해당 디렉토리 또는 파일이 숨김 처리되어 일반적인 ls 명령어로는 확인할 수 없습니다. 하지만 ls 명령어의 옵션으로 -a 를 붙여주면 숨김 처리된 디렉토리 및 파일을 확인할 수 있습니다.

**Work space** : Git의 세 가지 영역 중 하나로, Working tree 또는 Work tree라고도 하며, 눈으로 볼 수 있는 디렉토리 자체를 의미합니다.

Git은 Work space를 자동으로 스캔합니다. Git이 Work space를 스캔하다가 무언가 변경된 사항을 발견하면 사용자에게 해당 사항을 알려주고, 어떤 행위를 취해야 하는지 적절한 명령어 및 동작을 알려줍니다.

**파일들의 상태를 확인하기** : `git status`

파일의 상태
- Untracked: Git에 의해 파일의 상태가 추적되고 있지 않은 상태
- Tracked: 파일의 상태가 추적되고 있는 상태
  - Unmodified : 파일의 수정이 Git에 의해 감지되지 않은 상태
  - Modified : 파일의 수정이 Git에 의해 감지된 상태
  - Staged : 파일이 Staging area에 존재하는 상태

**Staging area**

Local repository에 저장할 파일들이 임시적으로 대기하는 영역을 의미합니다. 일반적으로 Git을 활용하여 작업을 할 때에는 Work space에서 작업을 마친 파일을 Staging area로 옮겨서 모아두고, 추후 어느 정도의 단위 작업이 끝나면 Staging area에 모인 파일들을 한 번에 Local repository로 저장합니다.

Local repository에 파일을 저장하는 것은 단순히 파일을 저장하는 것 이외의 특별한 의미를 가집니다. 따라서 Local repository에 파일들을 저장하기 전에 임시적으로 파일들을 모아둘 영역이 필요한데, 이것이 바로 Staging area입니다.

**Staging area로 파일을 이동시키기** : `git add`

특정 파일을 Staging area로 이동시킬 때에는 git add 파일_이름 명령어를 사용하면 됩니다. git add를 사용하면 파일이 Staging area로 이동하므로, `파일을 스테이징한다`고 표현하기도 합니다.

`git add .`를 입력하면 현재 디렉토리 내의 모든 파일이 스테이징됩니다.

**파일을 Local repository에 저장하고 버전을 기록하기** : `git commit`

git add를 통해 스테이징까지 마쳤다면, Commit을 할 수 있습니다. Commit이란, Local repository에 파일을 저장하는 행위를 가리키며, 파일을 Local repository에 저장함과 동시에 파일의 버전을 기록합니다.

```shell
git commit -m "First commit"
```

**Commit 내역 확인** : `git log`

git log를 입력하면 터미널 내에 별도의 창이 열립니다. `q`를 입력하여 빠져나올 수 있습니다.

**작업물을 Remote repository로 업로드하기** : `git push`

```shell
git push 원격_저장소_별칭 브랜치_이름 # origin main
```

1. Remote repository 만들기
2. Remote repository와 Local repository를 연결하기
3. 업로드하기


Remote Repository의 코드를 로컬로 복사해오기 : `git clone`

```shell
git clone 복사한_URL
```
### 3.2. GitHub workflow

1. Remote에 있는 다른 Repository에서 `fork`를 해서 Remote에 있는 내 Repository에 가지고 옵니다.
2. 이 코드를 수정하기 위해서는 내 컴퓨터로 가져오는 작업이 또 필요합니다. 내 컴퓨터에서 작업을 하기 위해서 `clone`을 합니다.
3. 이제 내 컴퓨터의 작업 공간(work space) 에서 작업에 들어간 파일들을 git의 관리하에 있는 상태로 올려줄 수 있습니다. 이 영역을 staging area라고 말합니다. 즉, staging area에 들어오지 않은 파일은 unstaged 혹은 untracked file이라고 말하며, staging area에 있는 파일들은 staged 된 파일이라고 말할 수 있습니다.
4. staging area에 들어온 파일들은 `commit`이 가능합니다. commit을 하고 나면 내 remote repository에 `push` 해서 commit 기록을 remote 에도 남겨줄 수 있습니다.
5. push를 완료한 후 이제 remote의 원래 레파지토리에 `pull request`를 보내면 Remote Repository로 내가 수정한 코드를 업로드할 수 있습니다.

## Reference

[Git 최초 설정](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95)

[git log에 대해 알아보기](https://dahye-jeong.gitbook.io/til/git/2019-01-09-git-log)

[ignore에 포함되어야할 목록](https://www.gitignore.io/)

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

