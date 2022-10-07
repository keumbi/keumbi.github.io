---
title: 블로그 시작!!
author: keumbi
date: 2022-10-01 21:20:00 +0900
categories: [Blogging, Tutorial]
tags: [github pages, error, setup]
---
<iframe allow="fullscreen" frameBorder="0" height="270" src="https://giphy.com/embed/G6cBtS3yWq7nyzNcl4/video" width="100%"></iframe>

## Overview
노션에 정리하던 내용들을 우선 블로그 페이지로 이사하려고 합니다.

## GitHub page 수정 확인 방법
git clone 경로(폴더) 이동 후 서버 시작하는 명령어 입력
```
bundle exec jekyll serve
```

정상적으로 확인된다면 http://127.0.0.1:4000/ 또는 http://localhost:4000/으로 접속하여 포스팅에 문제가 없는지 확인할 수 있다.
포스팅 내용 수정시 local jekyll 서버 재시작 필요 없지만, _config.yml 설정 파일 수정한 경우는 재시작 필요 ```Ctrl+c``` 눌러서 서버를 중지하고, ```bundle exec jekyll serve``` 명령어 다시 입력해서 재시작!! 원하는데로 수정 완료 됐다면, add, commit and push~

## Jekyll 4.2.0 Please append --trace to the serve command
```
bundle exec jekyll serve --trace
```

## Could not find gem 'webric x64-mingw32'
설치
```
gem install webrick
```
버전 업데이트
```
bundle exec jekyll serve
```
다시 빌드
```
jekyll build
```


<!--git checkout -b bugFix-->


```text
test
```
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

[크롬부가기능 추천](https://jojoldu.tistory.com/406?category=798573)

[PMD](https://velog.io/@been/IT%EA%B8%B0%EC%82%AC%EA%B0%9C%EB%B0%9C%EC%9E%90%EA%B0%80-%EA%B6%8C%EC%9E%A5%ED%95%98%EB%8A%94-Java-%EC%BD%94%EB%93%9C-%ED%92%88%EC%A7%88-%EB%8F%84%EA%B5%AC)

[글 쓸 시간을 따로 마련하기](https://wormwlrm.github.io/2022/08/20/Personal-Branding-from-Technical-Writing.html)
