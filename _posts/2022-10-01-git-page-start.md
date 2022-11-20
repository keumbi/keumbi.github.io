---
title: 블로그 GitHub Page로 다시 시작!!
author: keumbi
date: 2022-10-01 21:20:00 +0900
categories: [Error Handling Log]
tags: [github pages, error, setup]

---


![Window shadow](https://media4.giphy.com/media/1SzIPkhn8EOK99F0vj/giphy.gif){: .shadow style="max-width: 80%" }

## 이슈
부트캠프를 시작하고 벌써 계절이 바뀌고 시간이 점점 빠르게 가는 거 같습니다. 모든 크루분들이 블로그 기록에 대해 강조했던 부분이 있었습니다. Day1 메타인지에서 부터 강조했던, 자신의 언어로 배운 부분을 정리하는 것을 노션에 차곡차곡 쌓아 블로그에 멋지게 옮기려고 했지만... 정리하던 내용들을 우선 블로그 페이지로 옮겨두는 것으로 타협하고,  GitHub Page 세팅하면서 어려웠던 부분을 몇 자 적어 보았습니다.

## GitHub page 수정 확인 방법
git clone 경로(폴더) 이동 후 서버 시작하는 명령어 입력
```shell
bundle exec jekyll s
```

정상적으로 확인된다면 <http://127.0.0.1:4000/> 또는 <http://localhost:4000/>으로 접속하여 포스팅에 문제가 없는지 확인할 수 있습니다.
포스팅 내용 수정 시 local Jekyll 서버를 재시작할 필요가 없지만, _config.yml 설정 파일을 수정한 경우는 재시작 필요합니다. `Ctrl+c` 눌러서 서버를 중지하고, `bundle exec jekyll serve` 명령어 다시 입력해서 재시작!! 원하는데로 수정 완료됐다면, add, commit and push~

## 처음 시작했을때 만났던 에러 모음
아래의 문구가 터미널에 출력됐다면, 당황하지 말고, 구글링하면 대부분 해결할 수 있습니다.

### Jekyll 4.2.0 Please append --trace to the serve command
```shell
bundle exec jekyll serve --trace
```


## Could not find gem 'webric x64-mingw32'
설치 (시키는데로 하면 대부분 됨)
```shell
gem install webrick
```
버전 업데이트
```shell
bundle exec jekyll serve
```
다시 빌드
```shell
jekyll build
```
끝!!

## 좋은 커밋 메세지 어떻게 작성하지?
1. 50자 내외로 작성
2. 영문 작성시 첫 글자 대문자로 작성
3. 마침표 사용 안하기
4. 명령문 형태로 작성


**4.1. 명령문 형태로 작성 예제**

Refactor subsystem X for readability

Update getting started documentation

Remove deprecated methods

Release version 1.0.0

**For example:**

* If applied, this commit will <U>refactor subsystem X for readability</U>
* If applied, this commit will <U>update getting started documentation</U>
* If applied, this commit will <U>remove deprecated methods</U>
* If applied, this commit will <U>release version 1.0.0</U>
* If applied, this commit will <U>merge pull request #123 from user/branch</U>

**Notice how this doesn’t work for the other non-imperative forms:**

* If applied, this commit will ~~fixed bug with Y~~
* If applied, this commit will ~~changing behavior of X~~
* If applied, this commit will ~~more fixes for broken stuff~~
* If applied, this commit will ~~sweet new API methods~~

### TIP. Git Commit Comment Convention
**Tag Name**	Description

**Add**	새로운 파일 추가

**Feat**	새로운 기능 추가

**Fix**	버그 수정

**Docs**	문서 수정

**Style**	코드 formatting, 세미콜론 누락, 코드 변경이 없는 경우

**Design**	css 수정

**Rename**	파일 및 폴더 구조 변경

**Refactor**	코드 리팩토링

**Modify**	코드 단순 수정

**Test**	테스트 추가, 테스트 리팩토링

**Chore**	빌드 업무 수정, 패키지 매니저 수


<!--git checkout -b bugFix-->

<!--
블로그 마음 가짐
글 쓰기 전

글 쓸 시간을 따로 마련하기
쓸만한 글감은 미리 메모해두기
글의 장르 별 템플릿을 떠올리기
글의 초안을 작성하기
글 쓰는 중

제목으로 독자의 호기심을 끌기
서론으로 독자를 공감시키기
글 초반부에 요약 써두기
문단 수준에서 글 다듬기
문장 수준에서 글 다듬기
단어 수준에서 글 다듬기
미디어를 적절히 활용하기
글 쓴 후

글을 소리내어 읽기
주의를 환기시킨 후에 퇴고하기
글 발행 후

글을 공유하고 나의 구독자를 만들기
일관성을 유지하여 개인 브랜딩 구축하기
마무리-->

## Reference
[루비 설정 오류 해결](https://jojoldu.tistory.com/288)

[jekyll 오류 해결](https://velog.io/@minji-o-j/jekyll-%EC%98%A4%EB%A5%98-%ED%95%B4%EA%B2%B0)

[How to write a git commit message](https://cbea.ms/git-commit/)
