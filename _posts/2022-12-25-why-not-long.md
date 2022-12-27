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

*식별자가 0이라면, 실제로 값이 있고, 이 값이 식별자가 0임을 보장!!*



## Reference

[JPA Auditing 기능이란?](https://webcoding-start.tistory.com/53)
