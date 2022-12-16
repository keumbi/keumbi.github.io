---
title: Spring Security
author: keumbi
date: 2022-11-18 23:20:00 +0900
categories: [Framework, Spring]
tags: [week14, spring, spring security]
mermaid: true
---

## Overview
웹 사이트에 보안은 굉장히 중요한 요소입니다. Spring Framework에서는 Spring Security를 통해 보안 관련 기능을 편리하게 지원하고 있습니다.

> 학습목표
- Spring Security를 사용해야 하는 이유를 설명할 수 있다.
- Spring Security 환경 구성을 학습하고 직접 구성할 수 있다.
- Spring Security 인증(Authentication) 구성요소에 대해 이해할 수 있다.
- Spring Security 인가(또는 권한 부여, Authorization) 구성요소에 대해 이해할 수 있다.
{: .prompt-tip }

## 1. Spring Security란?
**Spring Security**는 Spring MVC 기반 애플리케이션의 인증(Authentication)과 인가(Authorization or 권한 부여) 기능을 지원하는 보안 프레임워크로써, Spring MVC 기반 애플리케이션에 보안을 적용하기위한 사실상의 표준입니다.

Spring에서 지원하는 Interceptor나 Servlet Filter를 이용해서 보안 기능을 직접 구현할 수 있지만 웹 애플리케이션 보안을 대부분의 기능을 Spring Security에서 안정적으로 지원하고 있기 때문에 구조적으로 잘 만들어진 검증된 Spring Security를 이용하는 것이 안전한 선택이라고 볼 수 있습니다.

### 1.1. Spring Security로 할 수 있는 보안 강화 기능

- 다양한 유형(**폼 로그인 인증**, **토큰 기반 인증**, **OAuth 2 기반 인증**, LDAP 인증)의 사용자 인증 기능 적용
- **애플리케이션 사용자의 역할(Role)에 따른 권한 레벨 적용**
- **애플리케이션에서 제공하는 리소스에 대한 접근 제어**
- **민감한 정보에 대한 데이터 암호화**
- SSL 적용
- 일반적으로 알려진 웹 보안 공격 차단

이 외에도 SSO, 클라이언트 인증서 기반 인증, 메서드 보안, 접근 제어 목록(Access Control List) 같은 보안을 위한 대부분의 기능을 지원합니다.

### 1.2. Spring Security에서 사용하는 용어 정리

Spring Security를 적용하기 위해서는 보안 영역에서 일반적으로 사용하는 개념들을 자주 접하게 됩니다.

따라서 이러한 개념들을 사전에 이해하고 있다면 Spring Security의 기능을 조금 더 쉽게 이해하고 적용할 수 있습니다.

- **Principal(주체)**
  - Spring Security에서 사용되는 `Principal`은 애플리케이션에서 작업을 수행할 수 있는 사용자, 디바이스 또는 시스템 등이 될 수 있으며, 일반적으로 인증 프로세스가 성공적으로 수행된 사용자의 계정 정보를 의미합니다.
- **Authentication(인증)**
  - `Authentication`은 애플리케이션을 사용하는 사용자가 본인이 맞음을 증명하는 절차를 의미합니다.
  - `Authentication`을 정상적으로 수행하기 위해서는 사용자를 식별하기 위한 정보가 필요한데 이를 `Credential`(신원 증명 정보)이라고 합니다.
  - 여러분이 특정 사이트에서 로그인을 위해 입력하는 **패스워드** 역시 여러분의 로그인 아이디를 증명하기 위한 `Credential`이 됩니다.
- **Authorization(인가 또는 권한 부여)**
  - `Authorization`은 Authentication이 정상적으로 수행된 사용자에게 하나 이상의 권한(authority)을 부여하여 특정 애플리케이션의 특정 리소스에 접근할 수 있게 허가하는 과정을 의미합니다.
  - `Authorization`은 반드시 Authentication 과정 이후 수행되어야 하며 권한은 일반적으로 역할(Role) 형태로 부여됩니다.
- **Access Control(접근 제어)**
  - `Access Control`은 사용자가 애플리케이션의 리소스에 접근하는 행위를 제어하는 것을 의미합니다.

### 심화 학습

- [세션 고정(session fixation) 공격](https://owasp.org/www-community/attacks/Session_fixation)
- [클릭재킹 공격](https://ko.wikipedia.org/wiki/%ED%81%B4%EB%A6%AD%EC%9E%AC%ED%82%B9)
- [CSRF](https://namu.wiki/w/CSRF)

## 2. Spring Security를 사용해야 하는 이유

- 보안 기능을 밑바닥부터 직접 구현하는 것보다 잘 검증되어 신뢰할 만한 Spring Security를 사용하는 것이 더 나은 선택이다.
- Spring Security는 특정 보안 요구 사항을 만족하기 위한 커스터마이징이 용이하고, 유연한 확장이 가능하다.

### 심화 학습

- [Apache Shiro](https://shiro.apache.org/)
- [OACC](http://oaccframework.org/)

## 3. Spring Security의 기본 구조

- Spring Security의 기본 구조와 기본적인 동작 방식을 이해하기 가장 좋은 인증 방식은 **폼 로그인 인증** 방식이다.
- Spring Security를 이용한 보안 설정은 `HttpSecurity` 를 파라미터로 가지고, `SecurityFilterChain` 을 리턴하는 Bean을 생성하면 된다.
- `HttpSecurity` 를 통해 Spring Security에서 지원하는 보안 설정을 구성할 수 있다.
- 로컬 환경에서 Spring Security를 테스트하기 위해서는 CSRF 설정을 비활성화 해야 한다.
- `InMemoryUserDetailsManager` 를 이용해 데이터베이스 연동없이 테스트 목적의 InMemory User를 생성할 수 있다.
- Spring Security에서 지원하는 InMemory User는 말 그대로 메모리에 등록되어 사용되는 User이므로 애플리케이션 실행이 종료되면 InMember User 역시 메모리에서 사라진다.
- InMemory User를 사용하는 방식은 **테스트 환경**이나 **데모 환경**에서 사용할 수 있는 방법이다.
- Spring Security는 사용자의 **크리덴셜(Credential, 자격증명을 위한 구체적인 수단)**을 암호화 하기 위한 PasswordEncoder를 제공하며, PasswordEncoder는 다양한 암호화 방식을 제공하며, Spring Security에서 지원하는 PasswordEncoder의 디폴트 암호화 알고리즘은 bcrypt이다.
- 패스워드 같은 **민감한(sensitive) 정보는 반드시 암호화 되어 저장되어야 합니다.**
  패스워드는 복호화 할 이유가 없기 때문에 **단방향 암호화** 방식으로 암호화 되어야 한다.
- Spring Security에서 `SimpleGrantedAuthority` 를 사용해 Role 베이스 형태의 권한을 지정할 때 `‘Roll_’ + 권한명` 형태로 지정해 주어야 한다.
- Spring Security에서는 Spring Security에서 관리하는 User 정보를 `UserDetails`로 관리한다.
- `UserDetails`는 UserDetailsService에 의해 로드(load)되는 핵심 User 정보를 표현하는 인터페이스입니다.
- `UserDetailsService`는 User 정보를 로드(load)하는 핵심 인터페이스이다.
- 일반적으로 Spring Security에서는 인증을 시도하는 주체를 `User(비슷한 의미로 Principal도 있음)`라고 부른다. Principal은 User의 더 구체적인 정보를 의미하며, 일반적으로 Username을 의미한다.
- Custom UserDetailsService를 사용해 로그인 인증을 처리하는 방식은 **Spring Security가 내부적으로 인증을 대신 처리해주는 방식이다.**
- `AuthenticationProvider`는 Spring Security에서 클라이언트로부터 전달받은 인증 정보를 바탕으로 인증된 사용자인지를 처리하는 Spring Security의 컴포넌트이다.


### 심화 학습
- [SSR(Server Side Rendering) 방식의 Controller 구현 방식](https://docs.spring.io/spring-framework/docs/current/reference/html/web.html#mvc-controller)
- [Ant Pattern](https://ant.apache.org/manual/dirtasks.html#patterns)
- [XML Name Space](https://www.w3schools.com/xml/xml_namespaces.asp)
- [Spring Security에서 제공하는 PasswordEncoder](https://docs.spring.io/spring-security/reference/features/authentication/password-storage.html#authentication-password-storage)
- [bcrypt 알고리즘](https://ko.wikipedia.org/wiki/Bcrypt)
- [단방향 암호화](https://en.citizendium.org/wiki/One-way_encryption)
- [EN.Clickjacking 공격](https://en.wikipedia.org/wiki/Clickjacking)
- [KO.Clickjacking 공격](https://ko.wikipedia.org/wiki/%ED%81%B4%EB%A6%AD%EC%9E%AC%ED%82%B9)


## 4. Spring Security의 웹 요청 처리 흐름

- Spring Security를 애플리케이션에 적용하는데 어려움을 겪는 가장 큰 이유 중에 하나는 Spring Security의 아키텍쳐와 **Spring Security의 컴포넌트들이 어떻게 인터랙션해서 인증, 권한 등의 보안 작업을 처리하는지 이해하지 못하기 때문이다.**
- **서블릿 필터(Servlet Filter)**는 서블릿 기반 애플리케이션의 엔드포인트에 요청이 도달하기 전에 중간에서 요청을 가로챈 후 어떤 처리를 할 수 있도록 해주는 Java의 컴포넌트이다.
- Spring Security의 필터는 클라이언트의 요청을 중간에서 가로챈 뒤, 보안에 특화된 작업을 처리하는 역할을 한다.
- `DelegatingFilterProxy`라는 이름에서 알 수 있듯이 **서블릿 컨테이너 영역의 필터와 ApplicationContext에 Bean으로 등록된 필터들을 연결해주는 브릿지 역할을 합니다.**
- **Spring Security의 Filter Chain**은 Spring Security에서 **보안을 위한 작업을 처리하는 필터의 모음이며, Spring Security의 Filter를 사용하기 위한 진입점이 바로 `FilterChainProxy`입니다.**


### 심화 학습

- [서블릿 필터](https://docs.oracle.com/javaee/7/api/javax/servlet/Filter.html)
- [Spring Security에서 지원하는 Filter](https://docs.spring.io/spring-security/reference/servlet/architecture.html#servlet-security-filters)

## 5. Filter와 FilterChain
<!--
mermaid
flowchart LR
  subgraph Client
    direction TB
    subgraph B1
        direction RL
        i1 -->f1
    end
    subgraph B2
        direction BT
        i2 -->f2
    end
  end
  A --> test --> B
  B1 --> B2
-->

### 5.1. Filter

서블릿 필터(Servlet Filter)는 서블릿 기반 애플리케이션의 엔드포인트에 요청이 도달하기 전에 중간에서 요청을 가로챈 후 어떤 처리를 할 수 있도록 해주는 Java의 컴포넌트입니다.

클라이언트가 서버 측 애플리케이션으로 요청을 전송하면 제일 먼저 **Servlet Filter**를 거치게 됩니다.

그리고 **Filter에서의 처리가 모두 완료되면** DispatcherServlet에서 클라이언트의 요청을 핸들러에 매핑하기 위한 다음 작업을 진행합니다.

### 5.2. Filter Chain

Filter Chain은 우리가 앞에서 살펴보았듯이 여러개의 Filter가 체인을 형성하고 있는 Filter의 묶음을 의합니다.

####  Filter와 Filter Chain의 특성

- Servlet FilterChain은 요청 URI path를 기반으로 HttpServletRequest를 처리합니다. 따라서 클라이언트가 서버 측 애플리케이션에 요청을 전송하면 서블릿 컨테이너는 요청 URI의 경로를 기반으로 어떤 Filter와 어떤 Servlet을 매핑할지 결정합니다.
- Filter는 Filter Chain 안에서 순서를 지정할 수 있으며 지정한 순서에 따라서 동작하게 할 수 있습니다.
- Filter Chain에서 Filter의 순서는 매우 중요하며 Spring Boot에서 여러 개의 Filter를 등록하고 순서를 지정하기 위해서는 다음과 같은 두 가지 방법을 적용할 수 있습니다.
    1. Spring Bean으로 등록되는 Filter에 `@Order` 애너테이션을 추가하거나 `Orderd` 인터페이스를 구현해서 Filter의 순서를 지정할 수 있습니다.
    2. `FilterRegistrationBean` 을 이용해 Filter의 순서를 명시적으로 지정할 수 있습니다.

#### Filter 인터페이스

```java
//  Servlet Filter의 기본 구조
public class FirstFilter implements Filter {
     // (1) `init()` 메서드에서는 생성한 Filter에 대한 초기화 작업
     public void init(FilterConfig filterConfig) throws ServletException {

     }

     // (2) `doFilter()` 메서드에서는 해당 Filter가 처리하는 실질적인 로직을 구현
     public void doFilter(ServletRequest request,
                          ServletResponse response,
                          FilterChain chain)
                          throws IOException, ServletException {
        // (2-1) request(ServletRequest)를 이용해 다음 Filter(2-2)의 chain.doFilter(request, response)가 호출되기 전에 할 수 있는 전처리 작업에 대한 코드를 구현

        // (2-2)
        chain.doFilter(request, response);

        // (2-3) response(ServletResponse)를 이용해 (2-2)의 chain.doFilter(request, response)가 호출된 이 후에 할 수 있는 후처리 작업에 대한 코드를 구현
     }

     // (3) `destroy()` 메서드는 Filter가 컨테이너에서 종료될 때 호출되는데 주로 Filter가 사용한 자원을 반납하는 처리 등의 로직을 작성
     public void destroy() {
        // (5) Filter가 사용한 자원을 반납하는 처리
     }
  }
```

### Filter 실습 예제

직접 Filter를 만들어서 애플리케이션을 실행시킨 후, Filter가 어떤식으로 동작하는지 직접 확인 할 수 있습니다.

1️⃣ **첫 번째 Filter 구현**


```java
import javax.servlet.*;
import java.io.IOException;

public class FirstFilter implements Filter {

    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
        Filter.super.init(filterConfig);
        System.out.println("FirstFilter 생성됨");
    }

    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
        System.out.println("========First 필터 시작========");
        chain.doFilter(request, response);
        System.out.println("========First 필터 종료========");
    }

    @Override
    public void destroy() {
        System.out.println("FirstFilter Destory");
        Filter.super.destroy();
    }
}
```


2️⃣ **FirstFilter를 적용하기 위한 FilterConfiguration 구성**


```java
import book.study.security.FirstFilter;
import org.springframework.boot.web.servlet.FilterRegistrationBean;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class FilterConfiguration {

    @Bean
    public FilterRegistrationBean<FirstFilter> firstFilterRegister()  {
        FilterRegistrationBean<FirstFilter> registrationBean = new FilterRegistrationBean<>(new FirstFilter());
        return registrationBean;
    }
}
```

Spring Boot에서 Servlet Filter는 FilterRegistrationBean의 생성자로 Filter 인터페이스의 구현 객체를 넘겨주는 형태로 등록할 수 있습니다.

3️⃣ **애플리케이션 실행**

애플리케이션을 실행하면 가장 먼저 init() 메서드가 실행되면서 아래와 같은 로그가 출력되는 것을 확인할 수 있습니다.

```java
FirstFilter 생성됨
```

Controller가 있다면 해당 컨트롤러의 핸들러 메서드로 요청을 보낸다면,

doFilter → controller 동작 → destroy 메서드의 형태로 Filter가 동작하면서 아마도 아래와 유사한 로그가 출력되는 것을 확인할 수 있습니다.

```java
========First 필터 시작========
Hello
========First 필터 종료========
```

4️⃣ **두 번째 Filter 구현**

이번에는 필터를 하나 더 구현해서 총 두 개의 Filter를 적용해 보도록 하겠습니다.

```java
import javax.servlet.*;
import java.io.IOException;

public class SecondFilter implements Filter {

    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
        Filter.super.init(filterConfig);
        System.out.println("SecondFilter가 생성되었습니다.");
    }

    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
        System.out.println("==========Second 필터 시작==========");
        chain.doFilter(request, response);
        System.out.println("==========Second 필터 종료==========");
    }

    @Override
    public void destroy() {
        System.out.println("SecondFilter가 사라집니다.");
        Filter.super.destroy();
    }
}
```

5️⃣ **FilterConfiguration에 두 번째 Filter 등록**


```java
import book.study.security.FirstFilter;
import book.study.security.SecondFilter;
import org.springframework.boot.web.servlet.FilterRegistrationBean;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class Config {

    @Bean
    public FilterRegistrationBean<FirstFilter> firstFilterRegister()  {
        FilterRegistrationBean<FirstFilter> registrationBean = new FilterRegistrationBean<>(new FirstFilter());
        registrationBean.setOrder(1); // (1)
        return registrationBean;
    }

    @Bean
    public FilterRegistrationBean<SecondFilter> secondFilterRegister()  {
        FilterRegistrationBean<SecondFilter> registrationBean = new FilterRegistrationBean<>(new SecondFilter());
        registrationBean.setOrder(2); // (2)
        return registrationBean;
    }

}
```


두 개의 Filter가 지정된 순서로 실행 되도록 (1), (2)와 같이 `registrationBean.setOrder()` 메서드로 순서를 지정할 수 있습니다.

`registrationBean.setOrder()`의 파라미터로 지정한 숫자가 적은 숫자일수록 먼저 실행됩니다.

애플리케이션을 다시 실행 시키고 Controller의 핸들러 메서드에 request를 전송하면 아래와 같은 실행 결과를 확인할 수 있습니다.

```java
========First 필터 시작========
==========Second 필터 시작==========
Hello
==========Second 필터 종료==========
========First 필터 종료========
```

**Filter는 나머지 Filter와 Servlet에 영향을 주기 때문에 Filter의 실행 순서가 중요!!**



### 핵심 포인트

- Spring Boot에서는 `FilterRegistrationBean` 을 이용해 Filter를 등록할 수 있다.
- Spring Boot에서 등록하는 Filter는 다음과 같은 방법으로 실행 순서를 지정할 수 있다.
  - Spring Bean으로 등록되는 Filter에 `@Order` 애너테이션을 추가하거나 `Orderd` 인터페이스를 구현해서 Filter의 순서를 지정할 수 있다.
  - `FilterRegistrationBean` 의 setOrder() 메서드를 이용해 Filter의 순서를 지정할 수 있다.

## Reference

[동일 사이트 및 동일 출처 이해하기](https://web.dev/same-site-same-origin/#same-site-cross-site)

[Starting Hello Spring Security Boot](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#getting-started)
