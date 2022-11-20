---
title: GitHub 페이지 자동 배포 실패
author: keumbi
date: 2022-11-02 9:20:00 +0900
categories: [Error Handling Log]
tags: [github pages, error, bug fix]
---

## 이슈
Run failed: Automatic build 깃허브 자동 배포 실패 메일이 왔다!! 블로그가 죽었다...

노션에 작성했던 글을 옮겨오는 과정에서 에러가 생겼나 하고, 한 땀 한 땀 자동 생성됐던 `NBSP`를 삭제했다.

또!! 에러 메시지를 잘 확인하지 않고 이거 삭제해 보고 저거 삭제해 보고 커밋만 열 번 한 것 같다. ㅠㅠ



## 에러 메시지

![에러 메세지](/assets/img/img-build-error.png)
```shell
* 1:13612: ERROR: Invalid first code point of tag name U+BA54.
```

![img.png](/assets/img/img-build-error2.png)
```shell
*  1:13628: ERROR: Invalid first code point of tag name U+BA54.

HTML-Proofer found 2 failures!

Error: Process completed with exit code 1.

```

## 해결 방법

> 메타인지는 현재 나의 인지 상태를 모니터링하는 능력이다. 모니터링 능력을 발달시키기 위해서는 자신이 무엇을 ‘어려워하는지’ 알아야 함과 동시에 ‘모를 수도 있다’는 사실을 인정해야 한다. 무언가를 모를 수 있다는 사실조차 인지하지 못한다면 모니터링과 컨트롤 능력을 제대로 키울 수 없다. 리사 손 \<메타인지 학습법\> 中

`\<메타인지 학습법\>` 열고 닫는 태그 사용 시 발생한 에러였다.

마크다운 문법에서 `>` 인용문 작성하는 기호인데 이 태그와 다른 html 태그가 섞여서 오류가 발생 되는 줄 알고 열심히 검색했는데 예전에 노션에 작성한 글이다 보니 \<메타인지 학습법\> 이런 게 내용 안에 있는지도 몰랐다. ㅠㅠ 각 `<`,`>` 앞에 `\`만 적어주면 끝!!

```markdown
\<메타인지 학습법\>
```

## TIP. 프로젝트 여러 파일 일괄 변경 단축키

`control` + `shift` + `r`


## Reference

[Parsing error: invalid-first-character-of-tag-name in expression.](https://github.com/vuejs/eslint-plugin-vue/issues/370)

[intellij 파일 내용 텍스트 일괄 변경하는 방법](https://yg-dad.tistory.com/1218)
