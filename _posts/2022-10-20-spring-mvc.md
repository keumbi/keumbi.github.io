---
title: Spring MVC 아키텍처
author: keumbi
date: 2022-10-20 20:20:00 +0900
categories: [Framework, Spring]
tags: [framework, section3, spring, spring mvc]
---

## Overview

Spring MVC가 무엇인지 그리고 Spring MVC의 동작 방식에 대해서 대략적으로 살펴보도록 하겠습니다.

## 1. Spring MVC란?
Spring에서 지원하는 모든 기능들을 포함해서 Spring Framework이라고 부릅니다.

Spring의 모듈 중에는 웹 계층을 담당하는 몇가지 모듈이 있습니다. 특히 **서블릿(Servlet) API**를 기반으로 클라이언트의 요청을 처리하는 모듈이 있는데, 이 모듈 이름이 바로 `spring-webmvc` 입니다.

개발자들 사이에서는 **Spring Web MVC**를 줄여서 **Spring MVC**라고 부르고 있고, Spring MVC가 **웹 프레임워크**의 한 종류이기 때문에 **Spring MVC 프레임워크**라고도 부릅니다.
- **Spring MVC는 클라이언트의 요청을 편리하게 처리해주는 프레임워크이다.**
- **우리가 만들게 될 샘플 애플리케이션은 Spring MVC가 제공해주는 기능을 이용해서 만든다.**

> 서블릿(Servlet)이란?
>
> 서블릿은 **클라이언트의 요청을 처리하도록 특정 규약에 맞추어서 Java 코드로 작성하는 클래스 파일**입니다.
>
> 그리고 **아파치 톰캣(Apache Tomcat)**은 이러한 서블릿들이 웹 애플리케이션으로 실행이 되도록 해주는 **서블릿 컨테이너(Servlet Container)** 중 하나입니다.
>
> 우리가 학습을 진행하면서 직접적으로 서블릿 기술을 사용할 일은 없지만 Spring MVC 내부에서는 서블릿을 기반으로 웹 애플리케이션이 동작한다는 사실은 기억을 하고 있으면 좋겠습니다.
>

그렇다면 Spring MVC에서 MVC는 무엇을 의미할까요? 지금부터 MVC의 의미를 살펴보도록 하겠습니다.

### 1.1. Model

**Model**은 Spring **M**VC에서 **M**에 해당됩니다.

Spring MVC 기반의 웹 애플리케이션이 클라이언트의 요청을 전달 받으면 요청 사항을 처리하기 위한 작업을 합니다.

이렇게 처리한 작업의 결과 데이터를 클라이언트에게 응답으로 돌려줘야하는데, 이 때 클라이언트에게 응답으로 돌려주는 **작업의 처리 결과 데이터**를 **Model**이라고 합니다.

> 클라이언트의 요청 사항을 구체적으로 처리하는 영역을 서비스 계층(Service Layer)이라고 하며, 실제로 요청 사항을 처리하기 위해 Java 코드로 구현한 것을 비즈니스 로직(Business Logic)이라고 합니다.
>

### 1.2. View

**View**는 Spring M**V**C에서 **V**에 해당됩니다.

**View는 앞에서 설명한 Model 데이터를 이용해서 웹브라우저 같은 클라이언트 애플리케이션의 화면에 보여지는 리소스(Resource)를 제공하는 역할을 합니다.**

Spring MVC에는 다양한 View 기술이 포함되어 있는데 View의 형태는 아래와 같이 나눌 수 있습니다.

- **HTML 페이지의 출력**
  - 클라이언트 애플리케이션에 보여지는 HTML 페이지를 직접 렌더링해서 클라이언트 측에 전송하는 방식입니다.
  - 즉, 기본적인 HTML 태그로 구성된 페이지에 Model 데이터를 채워 넣은 후, 최종적인 HTML 페이지를 만들어서 클라이언트 측에 전송해줍니다.
  - Spring MVC에서 지원하는 HTML 페이지 출력 기술에는 Thymeleaf, FreeMarker, JSP + JSTL, Tiles 등이 있습니다.
    > 하지만 이 방식은 프런트엔드와 백엔드가 통합된 구조이기 때문에 다루지 않습니다.

- **PDF, Excel 등의 문서 형태로 출력**
  - Model 데이터를 가공해서 PDF 문서나 Excel 문서를 만들어서 클라이언트 측에 전송하는 방식입니다.
  - 문서 내에서 데이터가 동적으로 변경되어야 하는 경우 사용할 수 있는 방식입니다.

- **XML, JSON 등 특정 형식의 포맷으로의 변환**
  - Model 데이터를 특정 프로토콜 형태로 변환해서 변환된 데이터를 클라이언트 측에 전송하는 방식입니다.
  - 이 방식의 경우 특정 형식의 데이터만 전송하고, 프런트엔드 측에서 이 데이터를 기반으로 HTML 페이지를 만드는 방식입니다.
  - 장점
    - 프런트엔드 영역과 백엔드 영역이 명확하게 구분되므로 개발 및 유지보수가 상대적으로 용이합니다.
    - 프런트엔드 측에서 비동기 클라이언트 애플리케이션을 만드는 것이 가능해집니다.

    > 우리가 앞으로 배우게 될 View 형태는 Model 데이터를 JSON 프로토콜 데이터로 변환하는 것입니다.


**JSON(JavaScript Object Notation)이란?**

JSON은 우리가 앞으로 학습하게 될 Spring MVC에서 클라이언트 애플리케이션과 서버 애플리케이션이 주고 받는 데이터 형식입니다.

과거에는 XML 형식의 데이터가 많이 사용되었으나 현재는 XML보다 상대적으로 가볍고, 복잡하지 않은 JSON 형식을 대부분 사용하고 있는 추세입니다.

- JSON의 기본 포맷
  - **`{”속성”:”값”}`** 형태입니다.


### 1.3. Controller

Controller는 Spring MV**C**에서 **C**에 해당됩니다.

**Controller는 클라이언트 측의 요청을 직접적으로 전달 받는 엔드포인트(Endpoint)로써 Model과 View의 중간에서 상호 작용을 해주는 역할을 합니다.**

즉, 클라이언트 측의 요청을 전달 받아서 비즈니스 로직을 거친 후에 Model 데이터가 만들어지면, 이 Model 데이터를 View로 전달하는 역할을 합니다.
```java

@RestController
@RequestMapping(path = "/v1/coffee")
public class CoffeeController {
private final CoffeeService coffeeService;

    CoffeeController(CoffeeService coffeeService) {
        this.coffeeService = coffeeService;
    }

    @GetMapping("/{coffee-id}")  // (1)
    public Coffee getCoffee(@PathVariable("coffee-id") long coffeeId) {
        return coffeeService.findCoffee(coffeeId); // (2)
    }
}
```

Spring MVC에서 Controller에 해당 되는 영역을 코드로 작성한 예입니다. **(Spring MVC의 사용법은 뒤에서 배울 예정이므로 지금은 몰라도 됩니다. 동작 흐름만 파악하세요)**

- (1)의 `@GetMapping` 애노테이션을 통해 클라이언트 측의 요청을 수신합니다.
- (2)에서 `CoffeeService` 클래스의 `findCoffee()` 메서드를 호출해서 비즈니스 로직을 처리합니다.

(2)에서 비즈니스 로직을 처리한 다음 리턴 받는 Coffee가 여기서는 **Model 데이터**가 됩니다.

그리고 `getCoffee()` 에서 이 **Model 데이터**를 리턴하는데, 리턴되는 이 **Model 데이터**는 우리가 코드 상에서는 확인할 수 없지만 내부적으로 **Spring의 View가 전달 받아서 JSON 포맷으로 변경**한 후에 클라이언트 측에 전달합니다.

**Model, View, Controller 간의 처리 흐름**

> Client가 요청 데이터 전송
>
>
> → Controller가 요청 데이터 수신 → 비즈니스 로직 처리 → Model 데이터 생성
>
> → Controller에게 Model 데이터 전달 → Controller가 View에게 Model 데이터 전달
>
> → View가 응답 데이터 생성
>

## 핵심 포인트

- Spring의 모듈 중에서 **서블릿(Servlet) API**를 기반으로 클라이언트의 요청을 처리하는 모듈이 바로 `spring-webmvc` 이다.
- spring-webmvc 모듈이 **Spring MVC**이다.
- Spring MVC는 **웹 프레임워크**의 한 종류이기 때문에 **Spring MVC 프레임워크**라고도 부른다.
- Spring MVC에서 **M**은 **Model**을 의미한다.
  - 클라이언트에게 응답으로 돌려주는 **작업의 처리 결과 데이터**를 **Model**이라고 한다.
- Spring MVC에서 **V**는 **View**를 의미한다.
  - View는 Model 데이터를 이용해서 웹브라우저 같은 클라이언트 애플리케이션의 화면에 보여지는 리소스(Resource)를 제공한다.
  - 우리가 실질적으로 학습하게 되는 View는 **JSON 포맷**의 데이터를 생성한다.
- Spring MVC에서 C는 **Controller**를 의미한다.
  - Controller는 클라이언트 측의 요청을 전달 받아 Model과 View의 중간에서 상호 작용을 해주는 역할을 담당한다.
- Spring MVC에서 MVC의 전체적인 동작 흐름은 다음과 같다.
  - Client가 요청 데이터 전송 → Controller가 요청 데이터 수신 → 비즈니스 로직 처리 → Model 데이터 생성 → Controller에게 Model 데이터 전달 → Controller가 View에게 Model 데이터 전달 → View가 응답 데이터 생성

## 2. Spring MVC의 동작 방식과 구성 요소
Spring MVC에서 클라이언트의 요청이 어떤 과정들을 거쳐서 Controller까지 전달 되는지 Spring MVC 내부의 동작 방식을 살펴보도록 하겠습니다.

Spring MVC의 요청과 응답 흐름에 대한 내부적인 동작 방식을 외울 필요는 없지만 **Spring MVC 구성 요소 간의 관계를 이해하고 있다면 실무에서 어떤 문제가 발생했을 때, 문제를 어디서부터 해결해야 될지에 대한 방법을 찾는 것이 조금 더 수월해집니다.**

![Spring MVC의 동작 방식 및 구성요소 애니매이션](/assets/img/img-spring-mvc.gif)


(1) 먼저 클라이언트가 요청을 전송하면 `DispatcherServlet`이라는 클래스에 요청이 전달됩니다.

(2) `DispatcherServlet`은 **클라이언트의 요청을 처리할 Controller에 대한 검색**을 HandlerMapping 인터페이스에게 요청합니다.

(3) `HandlerMapping`은 **클라이언트 요청과 매핑되는 핸들러 객체를 다시 DispatcherServlet에게 리턴**해줍니다.

> 핸들러 객체는 해당 핸들러의 Handler 메서드 정보를 포함하고 있습니다.
Handler 메서드는 Controller 클래스 안에 구현된 요청 처리 메서드를 의미합니다.
>

(4) 요청을 처리할 Controller 클래스를 찾았으니 이제는 **실제로 클라이언트 요청을 처리할 Handler 메서드**를 찾아서 호출해야 합니다. `DispatcherServlet`은 Handler 메서드를 직접 호출하지 않고, HandlerAdpater에게 **Handler 메서드 호출을 위임**합니다.

(5) `HandlerAdapter`는 DispatcherServlet으로부터 전달 받은 Controller 정보를 기반으로 **해당 Controller의 Handler 메서드를 호출**합니다.

이제 전체 처리 흐름의 반환점을 돌았습니다. 이제부터는 반대로 되돌아 갑니다.


(6) `Controller`의 Handler 메서드는 비즈니스 로직 처리 후 리턴 받은 **Model 데이터를 HandlerAdapter에게 전달**합니다.

(7) `HandlerAdapter`는 전달받은 **Model 데이터와 View 정보를 다시 DispatcherServlet에게 전달**합니다.

(8) `DispatcherServlet`은 전달 받은 View 정보를 다시 ViewResolver에게 **전달해서 View 검색을 요청**합니다.

(9) `ViewResolver`는 View 정보에 해당하는 View를 찾아서 **View를 다시 리턴**해줍니다.

(10) `DispatcherServlet`은 ViewResolver로부터 전달 받은 View 객체를 통해 Model 데이터를 넘겨주면서 클라이언트에게 전달할 **응답 데이터 생성을 요청**합니다.

(11) `View`는 응답 데이터를 생성해서 다시 DispatcherServlet에게 전달합니다.

(12) `DispatcherServlet`은 **View로부터 전달 받은 응답 데이터를 최종적으로 클라이언트에게 전달**합니다.

> DispatcherServlet의 역할
>
>
> Spring MVC의 요청 처리 흐름을 가만히 살펴보면 `DispatcherServlet`이 굉장히 많은 일을 하는 것처럼 보입니다.
>
> 클라이언트로부터 요청을 전달 받으면 HandlerMapping, HandlerAdapter, ViewResolver, View 등 대부분의 Spring MVC 구성 요소들과 상호 작용을 하고 있는 것을 볼 수 있습니다.
>
> 그런데 DispatcherServlet이 굉장히 바빠보이지만 실제로 요청에 대한 처리는 다른 구성 요소들에게 **위임(Delegate)**하고 있습니다.
>
> 마치 “HandlerMapping(핸들러매핑)아 Handler Controller 좀 찾아줄래? → ViewResolver(뷰리졸버)야 View 좀 찾아줄래? → View야 Model 데이터를 합쳐서 컨텐츠 좀 만들어 줄래?” 라고 하는것과 같습니다.
>
> 이처럼 DispatcherServlet이 애플리케이션의 가장 앞단에 배치되어 다른 구성요소들과 상호작용하면서 클라이언트의 요청을 처리하는 패턴을 **Front Controller Pattern**이라고 합니다.
>

Spring MVC의 동작 방식이 여러분들 머리속에 오래 기억되도록 요청 처리 흐름을 애니메이션으로 구성했으니, 기억이 나지 않으면 틈틈이 확인하면서 기억을 하길 바래봅니다.


## **핵심 포인트**

- Spring MVC의 요청 처리 흐름
  - 클라이언트의 요청을 제일 먼저 전달 받는 구성요소는 DispatcherServlet이다.
  - DispatcherServlet은 HandlerMapping 인터페이스에게 Controller의 검색을 위임한다.
  - DispatcherServlet은 검색된 Controller 정보를 토대로 HandlerAdapter 인터페이스에게 Controller 클래스내에 있는 Handler 메서드의 호출을 위임한다.
  - HandlerAdapter 인터페이스는 Controller 클래스의 Handler 메서드를 호출한다.
  - DispatcherServlet은 ViewResolver에게 View의 검색을 위임한다.
  - DispatcherServlet은 View에게 Model 데이터를 포함한 응답 데이터 생성을 위임한다.
  - DispatcherServlet은 최종 응답 데이터를 클라이언트에게 전달한다.
- DispatcherServlet이 애플리케이션의 가장 앞단에 배치되어 다른 구성요소들과 상호작용하면서 클라이언트의 요청을 처리하는 패턴을 **Front Controller Pattern**이라고 한다.


## Reference
 [Spring MVC 동작 방식 추가 설명](https://itvillage.tistory.com/entry/Spring-MVC%EC%9D%98-%EB%8F%99%EC%9E%91-%EB%B0%A9%EC%8B%9D-%EC%B6%94%EA%B0%80-%EC%84%A4%EB%AA%85)

