---
title: Java Math.max() 메서드 사0
author: keumbi
date: 2022-10-24 10:20:00 +0900
categories: [Language, Java]
tags: [java, method, max]

---

## Overview
Java.lang.math.max() 함수는 최대 두 개의 숫자를 반환하는 Java의 내장 함수입니다.
인수는 int, double, float, long 사용됩니다.
음수와 양수가 인수로 전달되면 양수 결과가 생성됩니다.
전달된 두 매개변수가 모두 음수이면 결과로 크기가 더 작은 숫자가 생성됩니다.


## 1. max() 사용하기
Syntax:

dataType max(dataType num1, dataType num2)

The datatypes can be int, float, double or long.

매개변수: 이 함수는 두 개의 매개변수 num1 및 num2를 받습니다.

그 중 최대값이 반환됩니다.

반환 값: 이 함수는 최대 두 개의 숫자를 반환합니다. 데이터 유형은 인수의 데이터 유형과 동일합니다.


### 1.1. double 사용 예시
```java
// Java program to demonstrate the use of max() function
// when two double data-type numbers are
// passed as arguments
public class Gfg {

    public static void main(String args[])
    {
        double a = 12.123;
        double b = 12.456;

        // prints the maximum of two numbers
        System.out.println(Math.max(a, b));
    }
}
```
Output:

12.456

### 1.2. 정수와 음수 사용 예시
```java
// Java program to demonstrate the use of max() function
// when one positive and one negative
// integers are passed as argument
public class Gfg {

  public static void main(String args[])
  {
    int a = 23;
    int b = -23;

    // prints the maximum of two numbers
    System.out.println(Math.max(a, b));
  }
}
```
Output:

23

### 1.2. 음수 사용 예시
```java

// Java program to demonstrate the use of max() function
// when two negative integers are passed as argument.
public class Gfg {

    public static void main(String args[])
    {
        int a = -25;
        int b = -23;

        // prints the maximum of two numbers
        System.out.println(Math.max(a, b));
    }
}
```
Output:

-23




## Reference
<https://www.geeksforgeeks.org/java-math-max-method-examples/>
