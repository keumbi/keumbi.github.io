---
title: Spring Framework의 특징
author: keumbi
date: 2022-10-11 21:20:00 +0900
categories: [Framework, Spring]
tags: [framework, section2, spring framework, spring core]
image:
path: /assets/img/img_spring_framework.png
width: 800
height: 500
alt: Framework
---

## Overview

Java 기반의 웹 애플리케이션을 만드는 다양한 기술들이 존재하는데, 그 중에서 여러분들이 앞으로 배워야 할 기술은 바로 **Spring Framework**이라는 오픈소스 기반의 기술입니다.

**Spring Framework(줄여서 Spring)**은 Java 기반의 웹 애플리케이션을 개발하는 개발자가 되기 위해서 반드시 익혀야 되는 핵심 중에 핵심 기술입니다.

## 1. Spring Framework 소개

### 1.1. Framework이란?

- 프로그래밍 상에서의 Framework은 기본적으로 프로그래밍을 하기 위한 어떠한 틀이나 구조를 제공한다.
- 장점
  - **효율적으로 코드를 작성할 수 있습니다.**
    - Framework이 라이브러리 형태로 제공함으로써 **개발자가 애플리케이션의 핵심 로직을 개발하는 것에 집중할 수 있도록** 해줍니다.
  - **정해진 규약이 있어 애플리케이션을 효율적으로 관리할 수 있습니다.**
- 단점
  - **내가 사용하고자 하는 Framework에 대한 학습이 필요합니다.**
  - **자유롭고 유연한 개발이 어렵습니다.**

### 1.2. Framework와 Library의 차이

- Framework은 개발자가 애플리케이션의 핵심 로직을 개발하는 것에 집중할 수 있도록 해준다.
- Library는 애플리케이션 흐름의 주도권이 개발자에게 있는 반면, Framework은 애플리케이션 흐름의 주도권이 개발자가 아닌 Framework에 있다.

### 1.3. Spring Framework이란?

1. **POJO(Plan Old Java Object)기반의 구성**
2. **DI(Dependency Injection) 지원**
3. **AOP(Aspect Oriented Programming, 관점지향 프로그래밍) 지원**
4. **Java 언어를 사용함으로써 얻는 장점**

Spring Framework을 학습함으로 인해서 **객체 지향 설계 원칙에 잘 맞는 재사용과 확장이 가능한 애플리케이션 개발 스킬을 향상**시킬 수 있다는 것, 그리고 **보다 나은 성능과 서비스의 안전성이 필요한 복잡한 기업용 엔터프라이즈 시스템을 제대로 구축하기 위한 능력**을 기를 수 있다.

### 1.4. Spring Framework을 배워야 하는 이유

- Spring Framework이 도입되기 전에는 JSP나 Servlet 기술을 사용한 Model1, Model2 아키텍쳐를 기반으로 한 Java 웹 애플리케이션을 제작하였다.
- Spring MVC 방식이 도입됨으로써 Java 웹 애플리케이션의 제작 방식이 획기적으로 변하게 되었다.
- Spring MVC 설정의 복잡함과 어려움을 극복하기 위해 Spring Boot이 탄생하게 되었다.

## 2. Spring Framework의 특징

![Spring 삼각형 - POJO 설명](/assets/img/img_pojo.png)

Spring 삼각형 - POJO 설명

### 2.1. POJO(Plain Old Java Object)

#### POJO는 알고보면 어려운 용어가 아니다.

POJO는 Plain Old Java Object 라는 단어의 첫글자를 따서 만든 약자입니다.

#### POJO 프로그래밍이란?

POJO 프로그래밍이란 POJO를 이용해서 프로그래밍 코드를 작성하는 것을 의미합니다.
그런데 단순히 순수 자바 객체만을 사용해서 프로그래밍 코드를 작성한다라고 해서 POJO 프로그래밍이라고 볼 수는 없습니다.

POJO 프로그래밍으로 작성한 코드라고 불리우기 위한 기본적인 규칙

1. **Java나 Java의 스펙(사양)에 정의된 것 이외에는 다른 기술이나 규약에 얽매이지 않아야 한다.**
2. **특정 환경에 종속적이지 않아야 한다.**

#### POJO 프로그래밍이 필요한 이유

POJO 프로그래밍이 필요한 이유는 앞에서 설명한 예시에 잘 나와 있습니다.

- 특정 환경이나 기술에 종속적이지 않으면 재사용 가능하고, 확장 가능한 유연한 코드를 작성할 수 있다.
- 저수준 레벨의 기술과 환경에 종속적인 코드를 애플리케이션 코드에서 제거 함으로써 코드가 깔끔해진다.
- 코드가 깔끔해지기 때문에 디버깅하기도 상대적으로 쉽다.
- 특정 기술이나 환경에 종속적이지 않기 때문에 테스트 역시 단순해진다.
- **객체지향적인 설계를 제한없이 적용할 수 있다.(가장 중요한 이유)**

### 2.2.  POJO와 Spring Framework의 관계

Spring은 POJO 프로그래밍을 지향하는 Framework

최대한 다른 환경이나 기술에 종속적이지 않도록 하기 위한 POJO 프로그래밍 코드를 작성하기 위해서 Spring에서는 세가지 기술을 지원 POJO를 감싸고 있는 **IoC/DI, AOP, PSA**

**애플리케이션 프로그래밍 코드를 작성할 때 항상 내가 작성한 코드가 객체지향스러운가에 대한 고민을 하는 습관을 가지는 것**

- POJO란 순수한 Java 객체를 의미한다.
- POJO 프로그래밍이란 순수 Java 객체가 다른 기술이나 환경에 종속되지 않도록 하기 위한 프로그래밍 기법이다.
- POJO 프로그래밍을 효과적으로 적용하기 위해서는 특정 기술에 대한 지식보다는 JDK의 API에 대한 지식과 객체지향적인 사고방식과 설계를 위한 훈련이 우선시 되어야 한다.
- Spring Framework은 POJO 프로그래밍을 지향하기 위해 IoC/DI, AOP, PSA 라는 기술을 제공한다.

### 2.3. IoC(Inversion of Control)

![Spring 삼각형 - IoC/DI 설명](/assets/img/img_ioc_di.png)

Spring 삼각형 - IoC/DI 설명

"Library는 애플리케이션 흐름의 주도권이 개발자에게 있고, Framework은 애플리케이션 흐름의 주도권이 Framework에 있다"라고 했습니다. **애플리케이션 흐름의 주도권이 뒤바뀐 것**을 바로 **IoC(Inversion of Control)**라고 합니다.

Spring에는 이 IoC의 개념이 어떻게 적용되어 있을까요?

답은 바로 **DI(Dependency Injection)**입니다.

### 2.4. DI(Dependency Injection) 의존성 주입

**IoC(제어의 역전)**는 서버 컨테이너 기술, 디자인 패턴, 객체 지향 설계 등에 적용하게 되는 일반적인 개념인데 반해 **DI(Dependency Injection)**는 IoC 개념을 조금 구체화 시킨 것이라고 볼 수 있습니다.

#### What(의존성 주입은 무엇일까요?)

객체지향 프로그래밍에서 의존성이라고 하면 대부분 객체 간의 의존성을 의미합니다.

클래스 끼리는 사용하고자 하는 클래스의 **객체를 생성해서 참조하게 되면 의존 관계가 성립**하게 됩니다.

두 클래스 간에 의존 관계는 성립 되었지만 아직까지 의존성 주입은 이루어지지 않았습니다.

생성자를 통해서 어떤 클래스의 객체를 전달 받는 것을 ‘**의존성 주입**’ 이라고 합니다.

생성자의 파라미터로 객체를 전달하는 것을 **외부에서 객체를 주입한다**라고 표현을 하는 것입니다.

#### Why(의존성 주입은 왜 필요할까요?)

일반적으로 Java에서 new 키워드를 사용해서 객체를 생성하는데, Reflection이라는 기법을 이용해서 Runtime시에 객체를 동적으로 생성할 수 있는 방법도 있다.

스텁(Stub)은 메서드가 호출되면 미리 준비된 데이터를 응답하는 것입니다. 즉, 고정된 데이터이기 때문에 몇 번을 호출해도 동일한 데이터를 리턴합니다. 몇번을 호출해도 동일한 데이터를 리턴하는 것을 전문 용어로 **멱등성(idempotent)**을 가진다 라고 합니다.

`new` 키워드를 사용해서 객체를 생성하게 되면 참조 할 클래스가 바뀌게 될 경우, 이 클래스를 사용하는 모든 클래스들을 수정할 수 밖에 없습니다.

이처럼 `new` 키워드를 사용해서 의존 객체를 생성할 때, 클래스들 간에 **강하게 결합(Tight Coupling)**되어 있다라고 합니다.

결론적으로 의존성 주입을 하더라도 의존성 주입의 혜택을 보기 위해서는 **클래스들 간의 강한 결합은 피하는 것이 좋아보입니다.**

**느슨한 결합(Loose Coupling)**이 필요할 때이군요.

> 애플리케이션의 요구사항은 언제든 변할 수 있기 때문에 코드를 작성할 때, ‘이렇게 작성해 놓으면 나중에 또 수정이 필요한 부분이 뭐가 있을까?’ 라는 생각은 한번 쯤 해보는게 좋다고 생각합니다


#### How(느슨한 의존성 주입은 어떻게 할까요?)

Java에서 클래스들 간의 관계를 느슨하게 만드는 대표적인 방법은 바로 **인터페이스(Interface)를 사용하는 것입니다.**

인터페이스 타입의 변수에 그 인터페이스의 구현 객체를 할당할 수 있는데 이를 **업캐스팅(Upcasting)**이라고 합니다.

이제 업캐스팅을 통한 의존성 주입으로 인해 MenuController와 MenuService는 **느슨한 결합 관계**를 유지하게 되었습니다.

#### Who(Spring 기반 애플리케이션에서는 의존성 주입을 누가 해줄까요?)

Spring 기반의 애플리케이션에서는 **Spring이 의존 객체들을 주입** 해주기 때문에 애플리케이션 코드를 유연하게 구성할 수 있습니다.

#### 핵심 포인트

- 애플리케이션 흐름의 주도권이 사용자에게 있지 않고, Framework이나 서블릿 컨테이너 등 외부에 있는 것 즉, 흐름의 주도권이 뒤바뀐 것을 **IoC(Inversion of Control)**라고 한다.
- **DI(Dependency Injection)**는 IoC 개념을 조금 구체화 시킨 것으로 객체 간의 관계를 느슨하게 해준다.
- 클래스 내부에서 다른 클래스의 객체를 생성하게 되면 두 클래스 간에 의존 관계가 성립하게 된다.
- 클래스 내부에서 `new`를 사용해 참조할 클래스의 객체를 직접 생성하지 않고, **생성자 등을 통해 외부에서 다른 클래스의 객체를 전달 받고 있다면 의존성 주입이 이루어 지고 있는 것**이다.
- `new` 키워드를 사용하여 객체를 생성할 때, 클래스 간에 **강하게 결합**(**Tight Coupling)**되어 있다고 한다.
- 어떤 클래스가 인터페이스 같이 일반화 된 구성 요소에 의존하고 있을 때, 클래스들 간에 **느슨하게 결합**(**Loose Coupling)**되어 있다고 한다.
- 객체들 간의 느슨한 결합은 요구 사항의 변경에 유연하게 대처할 수 있도록 해준다.
- 의존성 주입(DI)은 클래스들 간의 강한 결합을 느슨한 결합으로 만들어준다.
- Spring에서는 애플리케이션 코드에서 이루어지는 의존성 주입(DI)을 Spring에서 대신 해준다.


## Reference
추천 도서
[객체지향의 사실과 오해](http://www.yes24.com/Product/Goods/18249021)