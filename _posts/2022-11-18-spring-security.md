---
title: 인증 / 보안 기초
date: 2022-11-18 23:20:00 +0900
categories: [Framework, Spring]
tags: [github pages, week14, spring, spring security ]
published: false
---

## Overview
웹 사이트에 보안은 굉장히 중요한 요소입니다. Spring Framework에서는 Spring Security를 통해 보안 관련 기능을 편리하게 지원하고 있습니다.

> 학습목표
- Spring Security를 사용해야 하는 이유를 설명할 수 있다.
- Spring Security 환경 구성을 학습하고 직접 구성할 수 있다.
- Spring Security 인증(Authentication) 구성요소에 대해 이해할 수 있다.
- Spring Security 인가(또는 권한 부여, Authorization) 구성요소에 대해 이해할 수 있다.
{: .prompt-tip }

## 1. Spring security
HelloSpringSecurity라는 샘플 애플리케이션을 만들어보면서 Spring Security가 무엇인지 Spring Security를 왜 사용해야하는지를 이해하는 시간을 가져보겠습니다.

아울러 HelloSpringSecurity 애플리케이션을 통해 Spring Security에서 사용하는 보안에 대한 핵심 개념과 Spring Security의 동작 방식을 살펴보도록 하겠습니다.

> 학습목표
- Spring Security가 무엇인지 이해할 수 있다.
- Spring Security를 사용해야 하는 이유를 알 수 있다.
- Spring Security에서 사용하는 보안에 대한 핵심 개념을 이해할 수 있다.
- Spring Security의 기본 구조와 동작 방식을 이해할 수 있다.
{: .prompt-tip }

## 1.1. **Spring Security란?**

✅ 로그인 기능(**인증, Authentication**)이 없음

 0/0 0우리가 일반적으로 온라인 상에서 어떤 서비스를 이용할 때 ID/패스워드 같은 인증 정보를 사용하여 자격을 증명하는 로그인 기능이 없습니다.

로그인 기능이 없다면 어떤 문제가 발생할 수 있을까요?

나 자신을 증명할 방법이 없기 때문에 다른 사람이 회원으로 등록한 내 정보 또는 내가 주문한 주문 정보 등에 대해서 애플리케이션의 API를 호출해서 얼마든지 조회가 가능하게 됩니다.

한마디로 애플리케이션의 상태가 우리 집 대문에 자물쇠를 채우지 않은 상태로 활짝 열어놓은거나 마찬가지의 상태가 되는 것입니다.

이 상태로는 다른 사람의 개인정보를 탈취하는 것은 식은죽 먹기나 마찬가지일 것입니다.

✅ API에 대한 권한 부여(**인가, Authorization**) 기능이 없음

애플리케이션의 서비스를 사용하기 위한 적절한 인증 절차를 거쳤다하더라도 모든 리소스에 접근할 수 있는 것은 아닙니다.

예를 들어 단순히 커피를 주문하는 회원의 경우 커피 목록에서 커피를 조회해서 주문하고자 하는 커피를 선택한 후, 주문을 할 것입니다.

한 마디로 이 회원은 커피를 주문하는 손님인 것입니다.

그런데 손님이 매장에서 판매하는 커피 정보를 마음대로 등록할 수 없어야하는데 여러분이 만든 샘플 애플리케이션에서는 손님이 마음대로 커피 정보를 등록할 수 있습니다.

즉 API에 대한 접근 권한이 부여되지 않았기 때문입니다.

✅ 웹 보안 취약점에 대한 대비가 전혀 이루어지지 않았음

웹 애플리케이션을 위협하는 세션 고정 공격, 클릭재킹 공격, CSRF 등의 보안 취약점에 대한 고려가 전혀 이루어지지 않은 상태입니다.

이제 여러분들이 만든 샘플 애플리케이션에서 발생되는 보안 문제점을 해결해야 되는 시점인 것입니다.

바로 Spring Security라는 보안 프레임워크를 이용해서 말이죠.

> 세션 고정 공격, 클릭재킹 공격, CSRF에서 대해서 더 알아보고 싶다면 아래의 [심화 학습]을 참고하세요.
>

## Reference

[동일 사이트 및 동일 출처 이해하기](https://web.dev/same-site-same-origin/#same-site-cross-site)
