---
title: Section2, Week9, Day 34 TIL
author: keumbi
date: 2022-10-01 21:20:00 +0900
categories: [Look back, Day]
tags: [github pages, week9, spring framework, code states ]

---

## Daily to-do list

- [x]  Zoom- 굿모닝 세션
- [x]  Daily Coding
- [x]  Chapter- 실습 환경 구성
- [x]  점심시간
- [x]  Chapter 2 - Spring Framework의 특징

## 계획 단계
학습을 시작하기전 나의 현재 상태를 모니터링 해 봅시다. 아래 두 가지 질문에 대한 답을 천천히 생각해 본 후, 개인 블로그나 노트를 활용하여 기록합니다.

  ✅ **오늘 나의 학습 목표는 무엇인가요?**

  - Spring Framework이 무엇인지 이해할 수 있다.
  - Spring Framework을 왜 배워야하는지 이해할 수 있다.
  - Spring Framework의 아키텍처를 버드 아이 뷰 관점에서 이해할 수 있다.
  - Spring Framework 모듈이 무엇이고 Spring Framework에서 지원하는 모듈에는 어떤 것이 있는지 이해할 수 있다.
  - Spring Boot이 무엇이고 Spring Boot을 왜 사용해야하는지 이해할 수 있다.
  - **Chapter 1 - Spring Framework 소개**
    - Framework이 무엇인지 이해할 수 있다.
    - Spring Framework을 왜 배워야하는지 이해할 수 있다.
    - Spring Framework과 다른 Framework와의 차이를 이해할 수 있다.
  - **Chapter 2- Spring Framework 특징**
    - POJO(Plain Old Java Object)
      - POJO의 의미를 이해할 수 있다.
      - POJO가 필요한 이유를 알 수 있다.
    - IoC(Inversioin of Control)/DI(Dependency Injection)
      - IoC/DI의 의미를 이해할 수 있다.
      - IoC/DI가 필요한 이유를 알 수 있다.
    - AOP(Aspect Oriented Programming)
      - AOP의 의미를 이해할 수 있다.
      - AOP가 필요한 이유을 알 수 있다.
    - PSA(Portable Service Abstraction)
      - PSA의 의미를 이해할 수 있다.
      - PSA가 필요한 이유를 알 수 있다.

✅ **오늘 학습할 내용 중에 이미 알고 있는 내용은 무엇인가요?** 없다!! 어려울것 같다!! ㅜㅜ

✅ **굿모닝 세션**

**Q & A**

Q. id 값의 type이 int, PK, auto_increment를 설정해 주었을 때 int 값 범위를 넘어가면 overflow가 일어나나요?
overflow가 발생한다면 다시 처음부터 숫자 시작하나요?
다시 처음부터 시작하면서 값을 하나씩 증가시킬 때 겹치는 값이 생길 것 같을 때 DBMS가 알아서 걸러서 다른 값으로 넣어주나요?

A. [What happens when auto_increment on integer column reaches the max_value in databases?](https://stackoverflow.com/questions/2615417/what-happens-when-auto-increment-on-integer-column-reaches-the-max-value-in-data)


>스프링 프레임웍 객체지향을 잘 사용할 수 있게 만들어 주는 툴, 단순하게 기본적으로 제공된 것 만으로 구성, 종속적이지 않다. 좋은 설계 의존하는 객체가 무엇인지 몰라도 되는 것, 어떤 객체에 의존하든지 (인터페이스로 구현하면 됨)
프로젝트 안에 다양한 객체들이 서로 의존하고 있다.
인터페이스를 짜 놓고 시작하는 경우가 보통 (클래스 다룰 일이 거의 없다.) implements  다중상속 불가능
**IoC(Inversion of Control) DI(Dependency Injection 의존성 주입)** 제일 중요!! new 키워드 사용해서 사용했지만, 생성자 통해서 필더 주입 세터 주입 잘 사용 안 해서 생성자!!
왜 사용하는지 위주로 학습하기!! 핵심 개념 나중에 다시 반복해서 보기 (이틀로 DI 이해하기 어렵다) 실습을 거쳐야 필요성을 느낄 수 있음 완벽히 이해 어렵고 왜 사용하는지!!
> \
_위 내용은 짧은 시간에 지나가면 들었던 내용이라 틀린 내용일 수 있습니다. 혹시라도 잘못된 부분을 아신다면, 답글이나 메일로 말씀해 주신다면 Thx :)_


## Overview
**앞으로 만들어야 하는 소프트웨어는 서버에서 동작하는 Java 기반의 웹 애플리케이션**입니다.

Java 기반의 웹 애플리케이션을 만드는 다양한 기술들이 존재하는데, 그중에서 여러분들이 앞으로 배워야 할 기술은 바로 **Spring Framework**이라는 오픈소스 기반의 기술입니다.

**Spring Framework(줄여서 Spring)**은 Java 기반의 웹 애플리케이션을 개발하는 개발자가 되기 위해서 반드시 익혀야 하는 핵심 중에 핵심 기술입니다.

## 실습 환경 구성
실습 환경은 다음의 요구 조건이 필요합니다.

- PC에 JDK-11이 설치되어 있어야 합니다.
- 환경 변수에 JAVA_HOME 설정이 되어 있어야 합니다.
- PC에 IntelliJ Community Edition이 설치되어 있어야 합니다.


-  Spring Initializr [https://start.spring.io/](https://start.spring.io/) 공식 사이트로 이동합니다. Spring Initializr 공식 사이트에서는 여러분이 원하는 Spring Boot 실행 환경과 필요한 모듈을 손쉽게 포함하는 템플릿 프로젝트를 생성해줍니다.

![Window shadow](/assets/img/img_spring_framework.png){:  style="max-width: 90%" }
    _초기 세팅은 위 그림처럼 하면 됩니다._

1. Spring Boot 기반의 샘플 프로젝트 생성 <br>Spring Initializr [https://start.spring.io/](https://start.spring.io/) 공식 사이트로 이동합니다. Spring Initializr 공식 사이트에서는 여러분이 원하는 Spring Boot 실행 환경과 필요한 모듈을 손쉽게 포함하는 템플릿 프로젝트를 생성해줍니다.
2. 템플릿 프로젝트를 IntelliJ에서 열기 <br>[File] > [Open] 메뉴를 눌러서 압축 해제한 템플릿 프로젝트 폴더를 선택
3. Gradle Reload <br>[External Libraries] 하위에 의존 라이브러리들이 보이는지 확인합니다.
4. Lombok 설정 <br>[File] > [Settings] 창을 오픈합니다. <br>[Build, Execution, Deployment] > [Annotation Processors] 메뉴를 선택한 후, [Enable annotation processing] 체크 박스에 체크한 후, [Apply] 버튼과 [OK] 버튼을 차례차례 클릭합니다. <br>[Enable annotation processing] 체크 박스에 체크해야 Lombok을 정상적으로 사용할 수 있습니다.
5. Spring Boot Application 동작 확인

## Reference
[What is Normalization in DBMS (SQL)? 1NF, 2NF, 3NF Example](https://www.guru99.com/database-normalization.html)
<br>
[Database Normalization](https://www.w3schools.in/dbms/database-normalization)


## 🔥 데일리 회고 - 점검 및 평가

정규학습시간을 마친 후에는 정규학습시간 전에 개인 블로그나 노트에 적어둔 계획 단계에 대한 답변과, 아래 질문에 대한 답변을 블로그나 노트에 추가로 작성해 봅니다.

  ✅ **오늘 학습 내용 중 새롭게 배운 내용은 무엇인가요?** 스프링 프레임워크 사용하는 이유, 설치 방법, 특징

  ✅ **오늘 새롭게 학습한 내용을 다른 사람에게 설명할 수 있나요?** 할 수 없습니다!!

  ✅ **오늘 학습한 내용 중 아직 이해되지 않은 불확실한 내용은 무엇인가요?** 스프링 프레임워크 특징

  ✅ **이해되지 않은, 불확실한 내용을 보완하기 위해서 나는 무엇을 할 수 있을까요?** 실습을 해보고 다시 점검해 보겠습니다.

  ✅ **나의 오늘 학습 만족도는 몇점인가요?** 🌑🌘🌗🌖🌕  **→**  🌖
