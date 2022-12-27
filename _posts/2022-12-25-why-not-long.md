---
title: JPA 엔티티 Long을 사용하는가?
author: keumbi
date: 2022-12-25 22:20:00 +0900
categories: [Error Handling Log]
tags: [week20, spring, jpa]
published: false
---

## 이슈

```java

@Entity
public class Member {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
  //...
}
```

id 값으로 Long을 쓴다. 왜 long도 String도 아닌 Long인가?

-> id 타입이 long일 경우 `primitive type(원시 자료형)`이기 때문에 값이 없을 경우 0으로 초기화 된다. 그럼 id가 0일 때 고민이 생긴다. 실제로 이 값의 식별자가 0인건지, 아니면 값이 없어서 0인건지 알 수 없다.

## 해결

`wrapper class(래퍼 클래스)`인 Long을 사용할 경우 object type이기 때문에 nullable하므로 값이 없다면 null이 들어갈 수 있게 되어 null로 초기화가 된다.

**식별자가 0이라면, 실제로 값이 있고, 이 값이 식별자가 0임을 보장!!**

## 참고

**Wrapper Class 와 Null**

래퍼 클래스를 사용하면, 데이터 타입을 객체로 감싸주어(Boxing) 안에서 데이터를 관리할 수 있고, 그렇기 때문에 null을 데이터 값으로 받을 수 있다.

null 을 데이터 값으로 받을 수 있다는 것, 사용자로부터 들어온 값이 Null인지, 제대로 들어왔는지 바로바로 파악할 수 없다.

-> Null을 한번 더 체크 해야한다.

**Wrapper Class 올바른 사용법**

**어쩔 수 없이 Null을 다루어야할 때만 사용**

**1) DB에 값이 저장될 때**

- DB에는 값이 null로 들어갈 수 있기 때문에, 유연하게 값을 받을 필요가 있다.
- DB 테이블에 Null이 들어갔는지 아닌지, 판단할 수 없을 때, Wrapper Class를 사용하면 유용하다.

- null을 허용하지 않는 컬럼일 경우는, **기본 데이터타입**으로 지정

(예외)

**2) request로도 null이 들어올 때**

- Requeset 들어오는 값이 Null일 수 있기에 WrapperClass로 받아 줄 수있긴 하다.
- request같은 경우는 -> @validate, @NotNull같은 거로, 사전에 차단하는게 좋은 방법일 수 있다.

## Reference
[기본타입 vs 참조타입 with 래퍼클래스를 사용해야할 때 ➡️ Integer Wrapper Class 보다 int기본 타입](https://thalals.tistory.com/330)
[JPA 엔티티의 id로 Long을 사용하는 이유](https://shirohoo.github.io/spring/spring-data-jpa/2021-03-23-what-long/)
