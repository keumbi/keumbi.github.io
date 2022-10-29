---
title: Intellij 업데이트 후 한국어에서 영문으로 변경
author: keumbi
date: 2022-10-26 10:40:00 +0900
categories: [Error Handling Log]
tags: [git, gpg key, error, intellij]
---

## Overview
맥북 업데이트가 쏘아 올린 작은 공... 인텔리제이 업데이트 후 갑자기 한국어로 설정 변경됐다. 당황... 어색...

## 1. 플러그인에서 설정 변경하기
![인텔리제이 상단 모양 선택](/assets/img/img-intellij-top.png){:.shadow style="max-width: 60%" }

좌측 상단에 `Intellij IDEA` 선택 -> `Preference` 선택 (단축키 `cmd` + `,`)

좌측 메뉴에서 플러그인 선택 -> 설치된 플러그인 중 `kor` 검색 -> `Korean Language Pack / 한국어 언어 팩` 체크박스 해제

아래의 그림은 언어 팩이 비활성화된 상태입니다. 자세히 보시면, 체크박스가 해제돼있습니다.

아래의 그림처럼 체크박스를 해체하고, 적용 또는 확인 버튼을 누르면 됩니다.

인텔리제이 다시 시작하면 영문으로 다시 변경 완료!!

![플러그인에서 kor 검색](/assets/img/img-plugin-kor.png)


## 2. 자동 줄 바꿈으로 가로 스크롤 없애기 Soft Wrap 필요할 때

### 2.1. 에디터 창에서 라인 넘버 마우스 우클릭
에디터 창에서 라인 넘버스가 활성화돼 있다면, 오른쪽 클릭 혹은 `control` + `click`

![인텔리제이 에디터 화면에서 줄](/assets/img/img-intellij-num.png){:.shadow}

### 2.2. Soft-Wrap 체크
아래 그림과 같이 창이 떴다면, Soft-Wrap에 체크

![인텔리제이 에디터 팝업](/assets/img/img-intellij-pop-up.png){:.shadow}

아래 그림과 같이 자동 개행이  적용된다!!
![인텔리제이 에디터 적용 화면](/assets/img/img-intellij-soft-wrap.png)


### 2.3. 자동 줄바꿈으로 가로 스크롤 없애기 Soft Wrap 기본으로 적용
좌측 상단에 `Intellij IDEA` 선택 -> `Preference` 선택 (단축키 `cmd` + ` ``,`)

Editor -> General -> Soft Wraps
- [ ] Soft-wrap these files:->
- [x] Soft-wrap these files:
그리고 적용될 파일 적는칸에 자기가 원하는 파일 형식을 직접 적거나, 아래와 같이 모든 파일 적용을 이어서 적어준다.
```
;*
```
모든 파일에 자동 줄바꿈이 적용된다!!

![에디터 적용하기](/assets/img/img-intellij-editor-general.png){:.shadow}


## 3. ₩ → ` 설정 변경하는 방법
맥 OS 사용 시 **한글일 때 ₩**원화 표시가, **영어 때** `이 입력된다. (이걸 몰랐다!!!)

Wikipedia EN) The backtick ` is a typographical mark used mainly in computing. It is also known as backquote, grave, or grave accent.

Wikipedia KO) 백틱 `은 주로 컴퓨팅에서 사용되는 인쇄상의 표시입니다. 역따옴표, 억양 또는 억양 악센트라고도 합니다. 이 문자는 타자기가 기본 문자 위에 덮어써서 기본 문자에 억양을 추가할 수 있도록 설계되었습니다. 한국어로는 **억음부호**


### 3.3 KeyBindings 폴더 만들어서 적용하기

```
mkdir ~/Library/KeyBindings
```

DefaultkeyBinding.dict 파일 만들기

```
vi ~/Library/KeyBindings/DefaultkeyBinding.dict
```

설정 변경 내용 입력하기

```
{
    "₩" = ("insertText:", "`");
}
```

### 3.2. Karabiner-Elements 사용하기
```
brew install --cask karabiner-elements
```
[Karabiner-Elements complex_modifications rules](https://ke-complex-modifications.pqrs.org/#korean_won_to_backtick) 다른분이 적용해 둔 파일을 가져올 수 있다.

마이크로소프트 키보드 설정도 맥북에 맞게 원하는 기능으로 add item 버튼을 누르고 설정할 수 있다.
![키보드](/assets/img/img-karabiner-keyboard.png){:.shadow}

Karabiner-ElementsViewer에서 어떤 키가 입력되고 있는지 확인 할 수 있다.
입력 값을 확인하고, 수정할 수 있어서 한/영키나, 한자에 있는 키를 세팅하기 편하다.

## Reference
<https://ani2life.com/wp/?p=1753>
