---
title: Section1, Week2, Day 4 TIL
author: keumbi
date: 2022-08-24 21:20:00 +0900
categories: [Look back, Day]
tags: [week2, html, css, page layout ]
---

## Daily to-do list

- [x]  Zoom 굿모닝세션
- [x]  Chapter 페이지 레이아웃
- [x]  점심시간
- [x]  Chapter 페이지 레이아웃
- [x]  Chapter 웹 앱 화면 설계하기

## 계획 단계
학습을 시작하기전 나의 현재 상태를 모니터링 해 봅시다.
아래 두 가지 질문에 대한 답을 천천히 생각해 본 후, 개인 블로그나 노트를 활용하여 기록합니다.

✅ **오늘 나의 학습 목표는 무엇인가요?**

**페이지 레이아웃**

- 레이아웃을 위한 HTML 구조를 만들 수 있다.
- 손쉽게 웹 페이지의 각 요소를 정렬하는 데 Flexbox에 대한 핵심적인 개념과 내용을 이해할 수 있다.

**웹 앱 화면 설계하기**

- 만들고 싶은 앱의 와이어프레임을 그려볼 수 있다.
- 와이어프레임만 보고 HTML로 코딩할 수 있다.
- div 태그 또는 section, header 등의 시맨틱 태그로 영역을 구분하는 이유를 이해할 수 있다.
- HTML 문서에서 언제 id 혹은 class를 사용해야 하는지 이해할 수 있다.

✅ **오늘 학습할 내용 중에 이미 알고 있는 내용은 무엇인가요?**

개발환경 세팅 조금..


## Overview

HTML/CSS에 대한 지식을 바탕으로 **웹 사이트의 성격과 목적에 잘 맞게 필요한 요소들을 배치하는 작업과 관련된 페이지 레이아웃**에 대한 내용을 학습


> 학습목표
- 레이아웃을 위한 HTML 구조를 만들 수 있다.
- Flexbox에 대한 핵심적인 개념과 내용을 이해할 수 있다.
{: .prompt-tip }


## 1. 레이아웃: 화면 나누는 방법

### 1.1. HTML 구성하기

대부분 콘텐츠의 흐름은 좌에서 우, 위에서 아래로, CSS 화면 구분은 수직 분할, 수평 분할 차례대로 적용 콘텐츠 흐름에 따라 진행

**수직 분할:** 화면을 수직으로 구분, 콘텐츠 가로로 배치

**수평 분할:** 분할 된 요소를 수평으로 구분, 내부 콘텐츠가 세로로 배치될 수 있도록 함

#### 레이아웃 리셋

HTML 문서의 기본 스타일을 제거 CSS 코드

```css
* {box-sizing: border-box;}
body {margin:0; padding:0;}
```

### 1.2. Flexbox로 레이아웃 잡기

#### 박스를 유연하게 늘리거나 줄여 레이아웃을 잡는 방법

display: flex (부모 요소에 속성을 적용, 자식 박스의 방향과 크기를 결정하는 레이아웃 구성 방법)

1. flex-direction 정렬 축 정하기: row(기본 값), column, row-reverse, column-reverse
2. flex-wrap 줄 바꿈 설정:  nowrap(기본 값), wrap, wrap-reverse
3. justify-content 축 수평 방향 정렬 : row(기본 값), column

   flex-start, flex-end, center, space-between, space-around

4. align-items 축 수직 방향 정렬

   stretch, flex-start, flex-end, center, baseline

   flex-direction: row 인 경우

    1 2 3

    4 5 6

   flex-direction: column 인 경우

    1 4

    2 5

    3 6


#### 자식 요소에 적용하는 속성 (차지하는 공간과 관련)

flex: grow(팽창 지수), shrink(수축 지수), basis(기본 크기)

```css
flex: grow shrink basis;
flex: 0 1 auto;

flex-grow: 0; /* 정렬 축 방향으로 빈 공간이 있을 때, 남는 공간 차지 비율 */
flex-shrink: 1; /* 비율이 클수록 더 많이 줄어드는것 grow 속성과 함께 사용 지양 기본값 1 */
flex-basis: auto; /* 늘어나거나 줄어들기 전까지 기본 크기 */
```

- width와 flex-basis를 동시에 적용하는 경우, flex-basis가 우선됨
- 콘텐츠가 많아 자식 박스가 넘치는 경우, width가 정확한 크기를 보장 안함
- 콘텐츠가 많아 자식 박스가 넘치는 경우를 대비해, width 대신 max-width를 쓸 수 있음(flex-basis 사용X)
- Flexbox의  x축 Main axis  y축 Cross axis으로 구성됨 -항상 고정은 아님 Flex derection 사용하면 축을 전환 할 수 있음 (행, 열)

## 2. 와이어프레임 설계 및 목업 구현


> 학습 목표
- 만들고 싶은 앱의 와이어프레임 그릴 수 있다.
- 와이어프레임만 보고 HTML로 코딩할 수 있다.
- div 또는 section, header 등의 시맨틱 태그로 역영을 구분하는 이유를 이해한다.
- HTML 문서에서 언제 id 혹은 class를 사용해야 하는지 이해한다.
{: .prompt-tip }

**와이어프레임(Wireframe)**

레이아웃의 뼈대를 그리는 단계, 아주 단순하게, 레이아웃과 제품의 구조를 보여주는 용도

**목업(Mock-up)**

실물 크기의 모형을 뜻함. 실제 제품이 작동하는 모습과 동일하게 HTML 문서와 CSS를 작성함(기능적 동작 X)

**와이어프레임 설계 및 목업 구현**

## 3. 와이어 프레임 만들기

오븐(Oven), 피그마(Figma)와 미로(Miro) 등 여러 툴을 활용하여 와이어프레임을 작성



## Reference

[Flex-basis](https://developer.mozilla.org/ko/docs/Web/CSS/flex-basis)

[https://flexboxfroggy.com/#ko](https://flexboxfroggy.com/#ko)

[https://ovenapp.io/](https://ovenapp.io/)




## 🔥 데일리 회고 - 점검 및 평가

  아래 두 가지 질문에 대한 답을 천천히 생각해 본 후, 개인 블로그나 노트를 활용하여 기록합니다.정규학습시간을 마친 후에는 정규학습시간 전에 개인 블로그나 노트에 적어둔 계획 단계에 대한 답변과, 아래 질문에 대한 답변을 블로그나 노트에 추가로 작성해 봅니다.

✅ **오늘 학습 내용 중 새롭게 배운 내용은 무엇인가요?**

Flexbox로 레이아웃 잡기

✅ **오늘 새롭게 학습한 내용을 다른 사람에게 설명할 수 있나요?**

네!!

✅ **오늘 학습한 내용 중 아직 이해되지 않은 불확실한 내용은 무엇인가요?**

Flexbox 활용

✅ **이해되지 않은, 불확실한 내용을 보완하기 위해서 나는 무엇을 할 수 있을까요?**

Flexbox Froggy 해보기

✅ **나의 오늘 학습 만족도는 몇점인가요?** 🌑🌘🌗🌖🌕  **→**  🌕
