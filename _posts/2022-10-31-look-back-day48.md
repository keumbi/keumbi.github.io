---
title: Section3, Week12, Day 48 TIL
author: keumbi
date: 2022-10-31 21:20:00 +0900
categories: [Look back, Day]
tags: [github pages, week12, spring framework, code states ]
---


## Daily to-do list

- [x]  Zoom- 굿모닝 세션
- [x]  Daily Coding
- [x]  Chapter - Spring Data JDBC를 이용한 데이터 액세스 실습
- [x]  점심시간
- [x]  Chapter - Spring Data JDBC를 이용한 데이터 액세스 실습
- [x]  Pair - Spring Data JDBC를 이용한 데이터 액세스 실습
- [x]  Zoom - Checkpoint
- [x]  Survey - Pair Review & Unit Review

## 계획 단계

  ✅ **오늘 나의 학습 목표는 무엇인가요?**

Spring Data JDBC 기반 데이터 액세스 계층 연동 실습

✅ **오늘 학습할 내용 중에 이미 알고 있는 내용은 무엇인가요?**

Pagenation이 무엇인지 어떤 기능을 하는지...

✅ **굿모닝 세션**


## Overview
페이지네이션(Pagination)이란?

예를 들어, 데이터 베이스에 회원 정보가 100건이 저장되어 있는데 클라이언트 쪽에서 100건의 데이터를 모두 요청하는 것이 아니라 한 페이지에 일정 개수 만큼만 나누어서 달라고 요청하는 것을 페이지네이션(Pagination)이라고 합니다.

즉 page 번호가 1이고, 페이지에 포함되는 데이터의 개수가 10건일 경우,
데이터베이스의 테이블에서는 1 row부터 10 row까지만 조회되어야 합니다.

만약 page 번호가 2이고, 페이지에 포함되는 데이터의 개수가 10건일 경우,
데이터베이스의 테이블에서는 11 row부터 20 row까지만 조회되어야 합니다.

그런데 이렇게 조회를 하면 보통 가장 오래된 데이터부터 10건씩 조회되기 때문에 일반적으로 테이블의 row를 역순으로 10건씩 가져와서 최신 데이터부터 조회하는 경우가 대부분입니다.

## 페이지네이션(Pagination) 기능 구현
### **공통 제한 사항**

- MemberController 클래스 제한 사항
  - 페이지네이션(Pagination) 관련 구현은 아래 핸들러 메서드에 요청 전송 시, 적용되어야 합니다.
    - `MemberController`의 `getMembers()`
  - 페이지네이션(Pagination)이 적용되는 핸들러 메서드에서는 `@RequestParam` 애너테이션을 이용해 다음 파라미터를 전달 받아야 합니다.
    - page
      - 데이터 타입: `int`
      - 파라미터 역할: 페이지 번호
    - size
      - 데이터 타입: `int`
      - 파라미터 역할: 페이지 사이즈
      - 설명
        - 한 페이지에 포함되는 데이터 row의 개수입니다.
  - 파라미터인 page와 size는 아래와 같은 유효성 검증이 적용되어야 합니다.
    - page
      - 0보다 큰 숫자만 가능합니다.
    - size
      - 0보다 큰 숫자만 가능합니다.
- Response용 DTO 클래스 제한 사항 및 참고 사항
  - 제한 사항
    - `MemberController`클래스의 `getMembers()` 핸들러 메서드에서 리턴하는 Response용 DTO 클래스는 아래의 코드 h-1과 같은 구조를 갖는 응답 데이터를 클라이언트에게 전송해야 합니다.
  - 참고 사항
  - Response DTO 클래스는 현재 코드 상에 구현 되어 있는 MemberResponseDto 클래스를 반드시 사용할 필요는 없습니다.
  - 여러분이 별도의 공통 Response용 DTO 클래스를 만들어서 사용해도 무방합니다.
```json
{
    "data": [
        {
            "memberId": 20,
						"email": "hgd20@gmail.com",
            "name": "홍길동20",
            "phone": "010-2020-2020"
        },
        {
            "memberId": 19,
            "email": "hgd19@gmail.com",
            "name": "홍길동19",
            "phone": "010-1919-1919"
        },
        {
            "memberId": 18,
            "email": "hgd18@gmail.com",
            "name": "홍길동18",
            "phone": "010-1818-1818"
        },
        {
            "memberId": 17,
            "email": "hgd17@gmail.com",
            "name": "홍길동17",
            "phone": "010-1717-1717"
        },
        {
            "memberId": 16,
            "email": "hgd16@gmail.com",
            "name": "홍길동16",
            "phone": "010-1616-1616"
        },
        {
            "memberId": 15,
            "email": "hgd15@gmail.com",
            "name": "홍길동15",
            "phone": "010-1515-1515"
        },
        {
            "memberId": 14,
            "email": "hgd14@gmail.com",
            "name": "홍길동14",
            "phone": "010-1414-1414"
        },
        {
            "memberId": 13,
            "email": "hgd13@gmail.com",
            "name": "홍길동13",
            "phone": "010-1313-1313"
        },
        {
            "memberId": 12,
            "email": "hgd12@gmail.com",
            "name": "홍길동12",
            "phone": "010-1212-1212"
        },
        {
            "memberId": 11,
            "email": "hgd11@gmail.com",
            "name": "홍길동11",
            "phone": "010-1111-1111"
        }
    ],
    "pageInfo": {
        "page": 1,
        "size": 10,
        "totalElements": 20,
        "totalPages": 2
    }
}
```
- 위의 코드와 같이 현재 조회하는 page의 정보가 `pageInfo`에 포함되어야 합니다.
  - `page`
    - 데이터 타입: int
    - 설명
      - 페이지 번호
    - `size`
      - 데이터 타입: int
      - 설명
        - 한 페이지에 포함되는 데이터 row의 개수
    - `totalElements`
      - 데이터 타입: int
      - 설명
        - 테이블에 저장되어 있는 데이터의 총 개수
    - `totalPages`
      - 데이터 타입: int
      - 설명
        - 총 페이지 수
- 조회 되는 데이터는 코드 h-1과 같이 `memberId`를 기준으로 내림차순으로 표시되어야 합니다.
  - 즉 최신 데이터 순으로 표시되어야 합니다.
- 힌트
  - Spring 에서 지원하는 페이지네이션 API를 이용하면 의외로 손쉽게 실습을 완료할 수 있습니다.

## 🔥 점검 및 평가

정규학습시간을 마친 후에는 정규학습시간 전에 개인 블로그나 노트에 적어둔 계획 단계에 대한 답변과, 아래 질문에 대한 답변을 블로그나 노트에 추가로 작성해 봅니다.

  ✅ **오늘 학습 내용 중 새롭게 배운 내용은 무엇인가요?** Pagination 기능

  ✅ **오늘 새롭게 학습한 내용을 다른 사람에게 설명할 수 있나요?** 할 수 없습니다!!

  ✅ **오늘 학습한 내용 중 아직 이해되지 않은 불확실한 내용은 무엇인가요?** 혼자 할 수 있을까... ㅠㅠ

  ✅ **이해되지 않은, 불확실한 내용을 보완하기 위해서 나는 무엇을 할 수 있을까요?** 실습을 해보고 다시 점검해 보겠습니다.

  ✅ **나의 오늘 학습 만족도는 몇점인가요?** 🌑🌘🌗🌖🌕  **→**  🌖
