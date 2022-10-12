---
title: GitHub 페이지 대소문자 변경
author: keumbi
date: 2022-10-07 21:20:00 +0900
categories: [Blogging, Error Handling Log]
tags: [github pages, error, bug fix]
---
![Window shadow](https://media3.giphy.com/media/JsE9qckiYyVClQ5bY2/giphy.gif){: .shadow style="max-width: 60%" }

## Overview
블로그 초반에 세팅했던 명명규칙이 마음에 들지 않아 아무생각없이 파일 이름을 수정했다. 처음 파일을 만들었을때 `-` 줄표(dash)없이 대소문자로만 파일명을 만들고 싶었다. 깃허브에서 대소문자 변경시 에러가 발생하는것 같다. 로컬은 정상 작동 하지만, 같은 파일이 2개 되었다. 블로그 시작을 엄청 자랑하고 싶었던가...

## 터미널에서 입력
git 경로(폴더) 이동 후 아래 명령어 입력
```
git rm -r --cached .
git add --all .
git commit -a -m "Versioning untracked files"
git push origin master
//브랜치 이름이 main인 경우 master를 main으로 변경해야 함
```
## 마무리
파일 이름의 대소문자 변경하고 싶다면, 임의로 파일 이름 변경하지 말고, git 명령어를 사용해서 변경하세요.
gitFirst.md 파일을 git-first.md 이름 변경 예시
```
git mv gitFirst.md git-first.md
```


## Reference
[How do I commit case-sensitive only filename changes in Git?](https://stackoverflow.com/questions/17683458/how-do-i-commit-case-sensitive-only-filename-changes-in-git/17688308#17688308)



