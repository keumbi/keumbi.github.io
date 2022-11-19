---
title: Publishing HTML / CSS
author: keumbi
date: 2022-08-23 21:20:00 +0900
categories: [Language, HTML and CSS]
tags: [week2, publishing, html, css]
---


## Overview
웹 개발 관련 기술이 발전함에 따라 각 기술들의 내용이 점차 세분화되었고, 점차 복잡해지는 **웹 개발의 영역을 구분해야 할 필요성**이 생겨났습니다.

이런 배경에서 모던 웹 개발은 그 기능과 역할에 따라 보여지는 부분을 담당하는 프론트엔드와 보여지지 않는 부분을 담당하는 백엔드로 나뉘어졌고, 이에 따라 개발자들도 각 분야에 깊은 전문성을 가지는 프론트엔드 개발자와 백엔드 개발자로 구분되기 시작했습니다.

한편, 이러한 구분에도 불구하고, 각 영역의 개발자는 상대 영역의 기본적인 내용에 대해 필수적으로 이해해야 합니다. 즉, 프론트엔드 개발자라도 기본적인 백엔드 개발 지식을 알아야 하며, 반대로 **백엔드 개발자도 기본적인 프론트엔드 개발 지식에 대해 이해할 수 있어야** 합니다.

## 1. HTML


> 학습 목표
- HTML이 “구조를 표현하는 언어"라는 것을 이해하고, 기본 구조와 문법을 설명
- HTML이 마크업 언어라는 것
- 자주 사용하는 HTML 요소
- 시맨틱 태그란?
- 웹 문서를 HTML로 작성
{: .prompt-tip }


HTML(HyperText Markup Language): 웹 페이지를 구성하는 [마크업 언어](https://ko.wikipedia.org/wiki/%EB%A7%88%ED%81%AC%EC%97%85_%EC%96%B8%EC%96%B4) **전체적인 구조를 담당, 웹 페이지의 내용과 뼈대를 정해진 규칙대로 기술하는 언어**이다.
<details>
<summary>마크업 언어(markup 言語, markup language)</summary>

  마크업 언어는 태그 등을 이용하여 문서나 데이터의 구조를 명기하는 언어의 한 가지이다.<br><br>

  태그는 원래 텍스트와는 별도로 원고의 교정부호와 주석을 표현하기 위한 것이었으나 용도가 점차 확장되어 문서의 구조를 표현하는 역할을 하게 되었다. 이러한 태그 방법의 체계를 마크업 언어라 한다.<br><br>

  일반적으로 데이터를 기술하는 정도로만 사용되기에 프로그래밍 언어와는 구별된다. 다만 MXML 이나 XAML 처럼 특정 프로그래밍 언어와 강하게 연관되어 기능하거나 제한적으로 프로그래밍 언어의 기능을 갖춘 것도 일부 있는데, 이런 경우엔 구별이 명확하지 않다.
</details>

### 1.1. HTML의 기본 구조와 문법

- HTML은 문서의 틀이 되는 마크업 언어
- tag들의 집합
  - Tag는 &lt; &gt;로 묶인 기본 구성 요소
  - tag는 여는 태그 닫는 태그가 있지만 가끔 혼자 닫을 수 있음
  - tag에는 속성이 들어갈 수도 있음
- 트리 구조를 가짐

### 1.2. 자주 사용하는 HTML 요소

#### div

- 한 줄 차지

#### span

- 컨텐츠의 크기만큼 공간 차지

#### img

- 이미지 삽입
- 닫는 태그 없음!
- 속성을 통해 이미지 넣어줌

#### a

- 링크 삽입
- herf 속성을 통해 주소 입력
- target 을 통해서 새 창으로 열 수도 있음

#### ul, ol, li

- unordered list과 ordered list

#### input, textarea

- 다양한 입력 폼
- 여러가지 타입으로 input 만들기 가능

## 2. CSS와 프론트엔드 개발


> 학습 목표
- CSS 사용 목적 이해, 기본 문법과 구조 설명
- CSS 적용하는 방법에 대해 이해
- HTML 안에 CSS를 정의하는 것을 권장하지 않는 이유
- CSS를 이용해 텍스트 꾸미기
- 기본적인 CSS 박스 모델을 이해
- 레퍼런스 사이트를 이용해 CSS 속성을 검색 및 사용
{: .prompt-tip }


**CSS(Cascading Style Sheets):웹 페이지 스타일 및 레이아웃을 정의하는 스타일시트 언어** 인터페이스(Interface): 컴퓨터와 교류하기 위한 연결고리

### 2.1. 사용자 인터페이스(UI; User Interface)

컴퓨터의 복잡한 내부 작동원리를 이해하거나 CLI 명령어를 입력하지 못해도 일반 사용자가 쉽게 컴퓨터에게 의도한 행동을 명령할 수 있게 만든 인터페이스 앞에 "사용자"를 의미하는 User를 붙여 사용자 인터페이스라고 하며, 간편하게 UI라 부른다.

### 2.2. 좋은 사용자 경험(UX; User Experience)

사용자 인터페이스를 포함해서 사용자가 특정 서비스를 사용하면서 직/간접적으로 경험하면서 느끼는 종합적인 만족도를 의미하며 좋은 사용자 경험은 직관적이고 쉬운 UI에서 나온다.

### 2.3 CSS Selector



#### 셀렉터

```css
h1 { }
div { }
```

#### 전체 셀렉터

```css
* { }
```

#### Tag 셀렉터

```css
section, h1 { }
```

#### ID 셀렉터

```css
#only { }
```

#### class 셀렉터

```css
.widget { }
.center { }
```

#### attribute 셀렉터

```css
a[href] { }
p[id="only"] { }
p[class~="out"] { }
p[class|="out"] { }
section[id^="sect"] { }
div[class$="2"] { }
div[class*="w"] { }
```

#### 후손 셀렉터

```css
header h1 {}
```

#### 자식 셀렉터

```css
header > p { }
```

#### 인접 형제 셀렉터

```css
section + p { }
```

#### 형제 셀렉터

```css
section ~ p { }
```

#### 가상 클래스

```css
a:link { }
a:visited { }
a:hover { }
a:active { }
a:focus { }
```

#### 요소 상태 셀렉터

```css
input:checked + span { }
input:enabled + span { }
input:disabled + span { }
```

#### 구조 가상 클래스 셀렉터

```css
p:first-child { }
ul > li:last-child { }
ul > li:nth-child(2n) { }
section > p:nth-child(2n+1) { }
ul > li:first-child { }
li:last-child { }
div > div:nth-child(4) { }
div:nth-last-child(2) { }
section > p:nth-last-child(2n + 1) { }
p:first-of-type { }
div:last-of-type { }
ul:nth-of-type(2) { }
p:nth-last-of-type(1) { }
```

#### 부정 셀렉터

```css
input:not([type="password"]) { }
div:not(:nth-of-type(2)) { }
```

#### 정합성 확인 셀렉터

```css
input[type="text"]:valid { }
input[type="text"]:invalid { }
```

#### **CSS - 셀렉터 적용 순위**

1순위 declarations marked
2순위 inline
3순위 id
4순위 class
5순위 element selector (p,div,li,etc)
6순위 wildcard


### 2.4. 텍스트 꾸미기

- 절대 단위: px, pt 등
- 상대 단위: %, em, rem, ch, vw, vh 등

### 2.5. 박스 모델

**웹 페이지 내의 모든 콘텐츠는 고유의 영역**을 가지고 있다. 그 영역은 항상 직사각형으로 이루어져 있기 때문에, **박스(box)**라고 부른다.

**박스는 항상 직사각형이고, 너비(width)와 높이(height)를 가진다.** CSS를 이용해 속성과 값으로 그 크기를 설정한다.

#### 박스 구성요소

![박스 모델 예제](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model/boxmodel-(3).png)

[https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)

**레이아웃 디자인을 조금 더 쉽게 하는 방법: 여백과 테두리 두께를 포함한 박스 계산법**

```css
* {
  box-sizing: border-box;//모든 요소를 선택해 box-sizing 속성을 추가하고, border-box라는 값을 추가
}
```

모든 박스에서 여백과 테두리를 포함한 크기로 계산된다.  `box-sizing`을 일부 요소에만 적용하는 경우, 혼란을 가중시킬 수 있다.

- `content-box` 박스의 크기를 측정하는 기본 값, 그러나 대부분의 레이아웃 디자인에서 여백과 테두리를 포함하는 박스 크기 계산법인 `border-box`를 권장함


## Reference

[태그](https://ko.wikipedia.org/wiki/%ED%83%9C%EA%B7%B8_(%EC%A0%95%EB%B3%B4))

[프로그래밍 언어](https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4)

[MXML](https://ko.wikipedia.org/wiki/MXML)

[XAML](https://ko.wikipedia.org/wiki/XAML)
