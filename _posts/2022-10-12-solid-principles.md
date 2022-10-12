---
title: SOLID(객체 지향 설계 원칙)
author: keumbi
date: 2022-10-12 21:20:00 +0900
categories: [Blogging, TIL]
tags: [github pages, section2, solid principles]
image:
path: /assets/img/img_spring_framework.png
width: 800
height: 500
alt: Framework
---


## Overview
컴퓨터 프로그래밍에서 SOLID란 로버트 마틴이 2000년대 초반에 명명한 객체 지향 프로그래밍 및 설계의 다섯 가지 기본 원칙을 마이클 페더스가 두문자어 기억술로 소개한 것이다.
프로그래머가 시간이 지나도 유지 보수와 확장이 쉬운 시스템을 만들고자 할 때 이 원칙들을 함께 적용할 수 있다.
SOLID 원칙들은 소프트웨어 작업에서 프로그래머가 소스 코드가 읽기 쉽고 확장하기 쉽게 될 때까지 소프트웨어 소스 코드를 리팩터링하여 코드 냄새를 제거하기 위해 적용할 수 있는 지침이다.
이 원칙들은 애자일 소프트웨어 개발과 적응적 소프트웨어 개발의 전반적 전략의 일부다.

## 객체 지향 프로그래밍 및 설계의 다섯 가지 기본 원칙

단일 책임 원칙 (Single responsibility principle)
한 클래스는 하나의 책임만 가져야 한다.

개방-폐쇄 원칙 (Open/closed principle)
소프트웨어 요소는 확장에는 열려 있으나 변경에는 닫혀 있어야 한다.

리스코프 치환 원칙 (Liskov substitution principle)
프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 한다.

인터페이스 분리 원칙 (Interface segregation principle)
특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다.

의존관계 역전 원칙 (Dependency inversion principle)
프로그래머는 추상화에 의존해야지, 구체화에 의존하면 안된다. 의존성 주입은 이 원칙을 따르는 방법 중 하나다.



## EN wikipedia

This article is about the SOLID principles of object-oriented programming.
SOLID
Principles
Single responsibility
Open–closed
Liskov substitution
Interface segregation
Dependency inversion

In software engineering, SOLID is a mnemonic acronym for five design principles intended to make object-oriented designs more understandable, flexible, and maintainable. The principles are a subset of many principles promoted by American software engineer and instructor Robert C. Martin, first introduced in his 2000 paper Design Principles and Design Patterns.

### The SOLID ideas are

The single-responsibility principle: "There should never be more than one reason for a class to change." In other words, every class should have only one responsibility.
The open–closed principle: "Software entities ... should be open for extension, but closed for modification."
The Liskov substitution principle: "Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it." See also design by contract.
The interface segregation principle: "Clients should not be forced to depend upon interfaces that they do not use."
The dependency inversion principle: "Depend upon abstractions, `[not]` concretions."
The SOLID acronym was introduced later, around 2004, by Michael Feathers.

Although the SOLID principles apply to any object-oriented design, they can also form a core philosophy for methodologies such as agile development or adaptive software development.

## Learn SOLID Principles with CLEAN CODE Examples

<div class="iframe-container"><iframe src="https://www.youtube.com/embed/_jDNAf3CzeY" title="YouTube video player" allowfullscreen></iframe></div>

## Reference
[객체지향 설계 원칙](https://itvillage.tistory.com/entry/%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5-%EC%84%A4%EA%B3%84-%EC%9B%90%EC%B9%99-SOLID-%EC%9B%90%EC%B9%99)

[https://ko.wikipedia.org/wiki/SOLID(객체지향_설계)](https://ko.wikipedia.org/wiki/SOLID_(%EA%B0%9D%EC%B2%B4_%EC%A7%80%ED%96%A5_%EC%84%A4%EA%B3%84))

[https://en.wikipedia.org/wiki/SOLID](https://en.wikipedia.org/wiki/SOLID)

<https://www.digitalocean.com/community/conceptual-articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design#single-responsibility-principle>
