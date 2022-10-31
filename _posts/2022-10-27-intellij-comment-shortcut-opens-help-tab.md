---
title: Intellij 주석 단축키 사용 시
author: keumbi
date: 2022-10-26 10:40:00 +0900
categories: [Error Handling Log]
tags: [mac os, error, intellij, shortcut ]
image:
  path: /assets/img/img-so-bad.png
  alt: 단축키, 포커싱 이도, 다시, 에디터로, 이동
---

## Overview
인텔리제이에서 여러 줄 주석 단축키와 맥에서 제공하는 앱 단축키가 같아서 생기는 오류입니다. 단축키 입력 후 포커스가 help 탭으로 이동해서 살짝 거슬렸는데 맥북 업데이트로 변경이 많이 돼서 찾기가 너무 힘들었습니다. macOS Ventura를 사용 중이라면 아래 그림을 참조해서 체크박스를 해제하시면 됩니다. 업데이트... 아직 받지 마세요 ㅠㅠ


## 1. 주석 단축키 `shift` + `cmd` + `/` 사용 시 help 메뉴 활성화

### 1.1. 앱 단축키
시스템 설정 -> 키보드 -> 키보드 단축키 -> 앱 단축키

혹은 spotlight (`cmd` + `space bar`) **앱 단축키** 검색

### 1.2. 모든 응용 프로그램
 `>` 모든 응용 프로그램을 선택해서(선택하면 그림처럼 화살표 아이콘 방향이 아래를 향합니다.)

### 1.3. 도움말 메뉴 보기

하위 메뉴인 도움말 메뉴 보기 비활성화(체크박스 해제)


![설정 변경 ](/assets/img/img-mac-system.png){:.shadow}


## Conclusion
help 기능 단축키를 계속 이용하고 싶다면, 인텔리제이의 단축키를 변경해서 적용할 수 있습니다. 레퍼런스에 있는 내용을 참고해서 원하는 방식으로 변경하면 됩니다.

변경되기 전 Mac OS를 사용하고 있다면 레퍼런스 이미지가 더 도움이 될 것 같습니다.



## Reference

<https://stackoverflow.com/questions/38144396/intellij-comment-shortcut-opens-help-tab-on-the-mac-menu-bar>
