---
title: Spring Framework Validation
author: keumbi
date: 2022-10-21 21:20:00 +0900
categories: [Framework, Spring]
tags: [framework, section3, spring, spring MVC]

---

## Overview
사용자 입력을 검증하는 것은 대부분의 애플리케이션에서 매우 일반적인 요구 사항입니다.
Java Bean Validation 프레임워크는 이러한 종류의 검증을 처리하기 위한 사실상의 표준이 되었습니다.

## 1. Validation Annotations 사용하기

### 1.1. build.gradle에 의존성 추가 확인
```
implementation 'org.springframework.boot:spring-boot-starter-validation'
```

### 1.2. Validation Annotations 사용 예시
```java
import javax.validation.constraints.AssertTrue;
import javax.validation.constraints.Max;
import javax.validation.constraints.Min;
import javax.validation.constraints.NotNull;
import javax.validation.constraints.Size;
import javax.validation.constraints.Email;

public class User {

    @NotNull(message = "Name cannot be null")
    private String name;

    @AssertTrue
    private boolean working;

    @Size(min = 10, max = 200, message
      = "About Me must be between 10 and 200 characters")
    private String aboutMe;

    @Min(value = 18, message = "Age should not be less than 18")
    @Max(value = 150, message = "Age should not be greater than 150")
    private int age;

    @Email(message = "Email should be valid")
    private String email;

    // standard setters and getters
}
```

> `@NotNull` validates that the annotated property value is not null.

속성 값이 null이 아닌지 확인

> `@AssertTrue` validates that the annotated property value is true.

속성 값이 ture인지 확인

> `@Size` validates that the annotated property value has a size between the attributes min and max; can be applied to String, Collection, Map, and array properties.

속성 값이 min과 max 사이의 크기인지 확인, String, Collection, Map, array 속성에 적용가능

> `@Min` validates that the annotated property has a value no smaller than the value attribute.

속성 값이 value 보다 작은지 확인

> `@Max` validates that the annotated property has a value no larger than the value attribute.

속성 값이 value 보다 큰지 확인

> `@Email` validates that the annotated property is a valid email address.

속성 값이 유효한 이메일 주소인지 확인

> Some annotations accept additional attributes, but the message attribute is common to all of them. This is the message that will usually be rendered when the value of the respective property fails validation.

`message = "Age should not be less than 18"`메시지 속성은 모든 애너테이션에 사용할 수 있고, 해당 속성의 값이 유효성 검사에 실패할 때 일반적으로 렌더링되는 메시지입니다.


> `@NotEmpty` validates that the property is not null or empty; can be applied to String, Collection, Map or Array values.

속성 값이 null 또는 비어 있는지 확인, String, Collection, Map 또는 Array 값에 적용 가능

> `@NotBlank` can be applied only to text values and validates that the property is not null or whitespace.

텍스트 값에만 적용할 수 있으며 속성 값이 null 또는 공백이 아닌지 확인

> `@Positive` and `@PositiveOrZero` apply to numeric values and validate that they are strictly positive, or positive including 0.

두 에너테이션 모두 숫자 값에 적용되고, `@Positive`는 값이 양수인지 확인, `@PositiveOrZero`는 0을 포함하거나 양수인지 검증

> `@Negative` and `@NegativeOrZero` apply to numeric values and validate that they are strictly negative, or negative including 0.

두 에너테이션 모두 숫자 값에 적용되고, `@Negative`는 음수인지 확인, `@NegativeOrZero`는 0을 포함하거나 음수인지 검증

> `@Past` and `@PastOrPresent` validate that a date value is in the past or the past including the present; can be applied to date types including those added in Java 8.

두 에너테이션 모두 날짜 값에 적용되고, `@Past`는 과거인지, `@PastOrPresent`는 현재를 포함하거나 과거인지 검증, Java 8에 추가된 날짜 유형에 적용할 수 있다.

> `@Future` and `@FutureOrPresent` validate that a date value is in the future, or in the future including the present.
두 에너테이션 모두 날짜 값에 적용되고, `@Future`날짜 값이 미래인지, `@FutureOrPresent`는 현재를 포함하거나 미래인지 확인
The validation annotations can also be applied to elements of a collection: 컬렉션의 요소에도 적용할 수 있습니다.





## Reference
[Java Bean Validation Basics](https://www.baeldung.com/javax-validation)


