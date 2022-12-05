---
title: Java 기초
author: keumbi
date: 2022-08-30 21:20:00 +0900
categories: [Language, Java]
tags: [week3, java]
---


## Overview
코딩을 배우는 것은 외국어 학습과 비슷합니다. 문법을 달달 외운다고 영어를 잘할 수 있나요? 반드시 그렇지는 않습니다. 하지만 영어를 잘하는 사람은 문법에 알맞은 표현을 사용합니다.
자바를 사용하기 위해 반드시 알아야 하는 내용이지만, 그 자체를 달달 외운다고 코드를 잘 작성할 수 있는 것은 아닙니다. 우리의 목적은 실제로 동작하는 소프트웨어를 만드는 데에 있다는 것을 꼭 기억해주세요.

> 학습 목표
- 의사코드를 왜 작성하는지 이해할 수 있으며, 문제 해결을 위한 의사코드를 작성할 수 있다.
- 자바의 특징을 이해하고 기본적인 개발 환경을 설정할 수 있다.
- 자바의 기초 문법(타입, 변수, 상수 형 변환)을 이해할 수 있다.
- 자바의 기초 문법(연산자, 입/출력)과 제어문(조건문, 반복문)을 적용할 수 있다.
- 자바의 기초 문법을 활용하여 계산기를 구현할 수 있다.
{: .prompt-tip }

## 1. Java Intro

> 학습 목표
- 자바의 4가지 특징을 이해할 수 있다.
- JVM의 기능과 필요성을 이해할 수 있다.
- main 메서드가 무엇인지 이해한다.
{: .prompt-tip }

### 1.1. 자바의 특징

1. 운영체제에 독립적 - JRE(Java Runtime Environment: JVM(자바 가상머신) + 표준 클래스 라이브러리)가 설치되어 있는 모든 운영체제에서 실행 가능
2. 객체 지향 프로그래밍(Object Oriented Programming, OOP) 언어 - 여러 부품(객체)들을 만들고 조립하여 하나의 프로그램을 실행하는 개념
3. 함수형 프로그래밍 지원 - 람다식과 스트림 사용 컬렉션의 요소 필터링, 매핑, 집계 처리가 쉬워지고 코드가 간결해짐
4. 자동 메모리 관리(Garbage Collection) - 가비지 컬렉터(Garbage Collector)를 실행시켜 자동으로 사용하지 않는 메모리를 수거함

### 1.2. JVM과 JDK

자바는 컴파일러(Compiler)를 통해 기계어(Machine Language)로 변환되는 언어

- JRE(Java Runtime Environment) : JVM + 표준 클래스 라이브러리
- JDK(Java Development Kit) : JRE + 개발에 필요한 도구

JVM(Java Virtual Machine) - 자바 프로그램을 실행시키는 도구(프로그램을 실행하는 프로그램)

JDK(Java Development Kit) - 자바 프로그램 개발 시 필요 (OracleJDK와 OpenJDK가 있다)

### 1.3. Hello, World!


```java
public class Main {
  public static void main(String[] args) {

  }
}
```

`public class Main { … }` 접근 허용 범위가 public인 Main이라는 이름의 클래스를 정의 한다. => Main이라는 이름의 클래스가 있고, 그 안에서 코드를 작성

`public static void main (String[]args) { … }` 메서드를 정의하는 문법

메서드 - 어떤 기능을 하는 코드를 묶음으로 묶은 것(어떠한 기능을 수행하기 위한 일련의 코드들의 집합체)

함수 : 특정 기능을 수행하는 코드들을 묶은 것
메서드 : 클래스 내에 포함되어 있는 함수

자바는 객체지향 언어이며, 모든 코드를 클래스 내에 작성하기 때문에 보통 함수라는 용어보다는 메서드라는 용어를 사용함


**메서드란, ‘어떤 기능을 수행하기 위한 코드들을 묶어놓은 것’이며, 여기에서 ‘어떤 기능을 수행한다’는 것은 데이터를 입력받아 입력 받은 데이터에 일련의 처리를 가한 후, 그 결과값을 반환하는 것을 의미한다.**

메서드 정의

```text
반환_타입 메서드_이름(매개변수_타입 매개변수_이름) {
	메서드_바디
}
```

```java
int add(int number1, int number2) {
	return number1 + number2;
}
```

메서드 호출 - 메서드를 실행시키려면 메서드를 호출해주어야 함

```java
add(1, 2);
```

호출 연산자 `()`

`public static void main (String[]args) { … }`

main 메서드의 구조

- `void` : 반환 타입
- `main` : 메서드의 이름
- `String[]` : 매개변수의 타입
- `args` : 입력 데이터로 들어오는 값을 args라는 이름의 매개변수에 할당
- `{}` : 중괄호 블록 안에 코드 작성

**자바에서 `main` 메서드는 진입점 함수이며, 자바로 어떤 소스 코드를 작성할 때 반드시 `main` 메서드가 있어야 하고, `main` 메서드로부터 코드의 흐름이 시작됩니다.**

### 1.4. 의사코드 작성하는 방법

의사 코드(슈도코드 pseudo code) : 프로그래밍 언어로 코드를 작성하기 전에, 무엇을 어떤 과정을 통해 만들지 사람의 언어로 먼저 작성하는 것

예시) 사탕을 찾는 과정

네 개의 종이컵 중 하나에는 맛있는 사탕이 있다

사탕을 먹기 위해서는 사탕이 나올 때까지 종이컵을 하나씩 뒤집어 확인해야 함

네 개의 종이컵을 순서대로 뒤집어, 맛있는 사탕을 찾는다

```text
종이컵의 개수만큼, 종이컵을 하나씩 뒤집습니다
뒤집은 종이컵에 사탕이 있다면,
먹습니다
```

이 의사코드를 컴퓨터가 이해할 수 있는 프로그래밍 언어로 작성한다면

```java
for(int cupNumber=1; cupNumber<=4; cupNumber++){ // 4개의 컵을 하나씩 확인하면서
	if (candy) { // 만약 사탕이 있다면
		eat(); // 먹는다
	}
}
```

## 2. 변수(Variable)와 타입(Type)

> 학습 목표
- 타입의 개념을 이해하고 설명할 수 있다.
- 기본 타입과 참조 타입의 차이를 설명할 수 있다.
- 정수 타입, 실수 타입, 논리 타입, 문자 타입을 이해한다.
- 변수, 상수, 리터럴이 무엇인지 설명할 수 있다.
- 자동 타입 변환이 어떤 경우에 발생하는지 설명할 수 있다.
- 수동 타입 변환을 어떤 경우에 사용할 수 있는지, 그리고 어떻게 사용할 수 있는지 설명할 수 있다.
{: .prompt-tip }

### 2.1. 변수(Variable)

변수(Variable) : 값이 변할 수 있는 데이터를 임시적으로 저장하기 위한 수단

변수 정의 : 값을 저장할 수 있는 메모리 공간에 사람이 식별할 수 있는 이름을 붙인 것

변수 선언: 어떤 값을 저장할 메모리 공간을 확보하고, 해당 메모리 공간을 식별할 수 있는 이름을 붙이는 것

값 할당 또는 대입: 변수에 값을 저장하는 것 대입 연산자 `=` 를 사용함

```java
class Example {
	public static void main(String[] args) {
		int num; // 변수 선언
		num = 1; // 값 할당(초기화)
		num = 2; // 값 할당(재할당)

		int num2 = 1; // 선언과 동시에 초기화
	}
}
// 변수 num은 int형 → int형은 4byte → 4byte의 메모리 공간을 확보
```

**변수 명명 규칙:**  일반적으로 카멜 케이스(camelCase) 사용 `int camelCase;`

1. 영문자, 숫자, `_`, `$`를 사용할 수 있으며, 영문자는 대소문자가 구별되어 인식
2.  숫자로 시작하는 변수명은 사용할 수 없음
3. 자바에서 이미 사용 중인 는 변수명으로 사용할 수 없음

### 2.2. 상수(Constant)

상수(Constant) : 변하지 말아야 할 데이터를 임시적으로 저장하기 위한 수단(재할당 금지) `final`이라는 키워드를 사용해 선언할 수 있으며, 관례적으로 대문자에 언더바(_)를 넣어 구분하는 SCREAMING_SNAKE_CASE를 사용

#### 상수를 사용하는 이유

- 프로그램이 실행되면서 값이 변하면 안되는 경우
- 코드 가독성을 높이고 싶은 경우
- 코드 유지관리를 손쉽게 하고자 하는 경우

```java
// 기존 코드
final double CALCULATOR_PI  = 3.14;

// 변경된 코드
final double CALCULATOR_PI  = 3.14159;
```


### 2.3. 타입

어떤 값의 유형 및 종류를 의미하며, 타입에 따라 **값이 차지하는 메모리 공간의 크기**와, **값이 저장되는 방식**이 결정됨

#### 기본 타입과 참조 타입

**기본 타입(primitive type)**
  - 값을 저장할 때, 데이터의 **실제 값**이 저장
  - 정수 타입(byte, short, int, long), 실수 타입(float, double), 문자 타입(char), 논리 타입(boolean)

**참조 타입(reference type)**
  - 값을 저장할 때, 데이터가 저장된 곳을 나타내는 **주소값**이 저장

```java
public class Example {
    public static void main(String[] args) {
        int primitive = 1; // 기본타입변수 = 1;
        Object reference = new Object(); // 참조타입변수 = 객체;

        System.out.println(primitive); // 출력(기본타입변수);
        System.out.println(reference); //	출력(참조타입변수);
    }
}
// 1
// java.lang.Object@626b2d4a
```

### 2.3. 리터럴

문자가 가리키는 값 그 자체

```java
// 정수형 리터럴 20을 정수형 변수 currentAge에 할당
int currentAge = 20;

// 실수형 리터럴 3.14159를 실수형 변수 pi에 할당
double pi = 3.14159;

// 논리형 리터럴 true를 논리형 변수 boolean에 할당
boolean isGenius = true;

// 문자형 리터럴 'A'를 문자형 변수 firstAlphabet에 할당
char firstAlphabet = 'A';

// 문자열 리터럴 "CodeStates"를 문자열 타입 변수 learnedAt에 할당
String learnedAt = "CodeStates";
```

1. `float` 타입의 변수에 실수형 리터럴을 할당할 때, 리터럴 뒤에 접미사 `f`
2. `long` 타입의 변수에 정수형 리터럴을 할당할 때, 리터럴 뒤에 접미사 `L` (숫자와의 혼동을 방지하기 위해 보통 대문자 `L`을 사용)

### 2.4. 정수 타입

정수 타입은 숫자를 나타내는 타입으로, `byte`, `short`, `int`, `long` 의 총 4개의 타입

| 타입 | 메모리 | 표현 범위 |
| --- | --- | --- |
| byte | 1byte | -128(-27) ~ 127(27 - 1) |
| short | 2byte | -32,768(-215) ~ 32,767(215 - 1) |
| int | 4byte | -2,147,483,648(-231) ~ 2,147,483,647(231 - 1) |
| long | 8byte | -9,223,372,036,854,775,808(-263) ~ 9,223,372,036,854,775,807(263 - 1) |

```java
// 각 데이터 타입의 표현 범위에 맞는 값을 할당하고 있습니다.
byte  byteNum  = 123;
short shortNum = 12345;
int   intNum   = 123456789;
long  longNum  = 12345678910L;

// 각 데이터 타입의 표현 범위에 벗어난 값을 할당하고 있어 에러가 발생합니다.
byte  byteNum  = 130;
short shortNum = 123456;
int   intNum   = 12345678910;

// 숫자가 길면 언더바로 구분할 수 있습니다.
int   intNum   = 12_345_678_910;
long  longNum  = 12_345_678_910L;
```

**데이터 타입의 크기와 표현 범위**

`byte` → `short` → `int` → `long`으로 갈수록 데이터 타입의 크기도 커지고 표현 범위도 커진다.

→ **데이터 타입의 크기가 데이터의 표현 범위를 결정**

**정수형의 오버플로우와 언더플로우**

작성한 코드가 실행중일 때, 어떤 값이 실수로 작성한 코드에 의해 각 타입의 표현 범위를 넘어서는 경우가 발생

**오버플로우**
  - 자료형이 표현할 수 있는 범위 중 최대값 이상의 값을 표현한 경우 발생
  - 최대값을 넘어가면 해당 데이터 타입의 최소값으로 값이 순환
  - 예 : 어떤 값이 `byte`형이고, `byte`형의 최대값인 127을 값으로 가지는 경우, 이 값에 1을 더하면 128이 되는게 아니라, 최소값인 -128

**언더플로우**
  - 자료형이 표현할 수 있는 범위 중 최소값 이하의 값을 표현한 경우 발생
  - 최소값을 넘어가면 해당 데이터 타입의 최대값으로 값이 순환
  - 예 : 어떤 값이 `byte`형이고, `byte` 형의 최소값인 -128을 값으로 가지는 경우, 이 값에 1을 빼면 -129가 되는게 아니라, 최대값인 127

### 2.5. 실수 타입

실수는 소수점을 가지는 값을 의미하며, `float`형과 `double`형으로 분류

| 타입 | 메모리 | 표현 범위 | 정밀도 |
| --- | --- | --- | --- |
| float | 4byte | 음수 : -3.4 * 1038 ~ -1.4 * 10-45양수 : 1.4 * 10-45 ~ 3.4 * 1038 | 7자리 |
| double | 8byte | 음수 : -1.8 * 10308 ~ -4.9 * 10-324양수 : 4.9 * 10-324 ~ 1.8 * 10308 | 15자리 |

`double`형 리터럴에는 접미사 `d`를 붙여도, 붙이지 않아도 되지만, `float`형 리터럴에는 반드시 접미사 `f`를 붙여주어야 함

```java
// float형 리터럴을 float형 변수에 할당
float num1 = 3.14f;

// double형 리터럴을 double형 변수에 할당
double num2 = 3.141592d;
double num2 = 3.141592;
```

`double`형은 `float`형보다 더 큰 실수를 저장할 수 있고, 더  정확하게 저장할 수 있다.

**실수형의 오버플로우와 언더플로우**

실수형에서도 오버플로우와 언더플로우가 발생합니다. 다만, 오버플로우와 언더플로우가 발생했을 때의 결과가 다름

**오버플로우**
  - 값이 음의 최소 범위 또는 양의 최대 범위를 넘어갔을 때 발생하며, 이 때 값은 **무한대**

**언더플로우**
  - 값이 음의 최대 범위 또는 양의 최소 범위를 넘어갔을 때 발생하며, 이 때 값은 **0**

### 2.6. 논리 타입

`boolean`형은 참 또는 거짓을 저장할 수 있는 데이터 타입으로, 오직 `true` 혹은 `false`를 값으로 가짐

단순히 참과 거짓을 표현하기 위해서는 1bit만 있으면 되지만, JVM이 다룰 수 있는 데이터의 최소 단위가 1byte이기 때문에 `boolean`형은 1byte(8bit)의 크기를 가진다.

```java
boolean isRainy = true;
boolean isAdult = false;
```

### 2.7. 문자 타입

`char`(2byte) 변수를 선언하면 해당 변수에 오직 하나의 문자형 리터럴을 저장할 수 있다.

문자형 리터럴을 작성할 때에는 반드시 큰 따옴표(`””`)가 아닌 작은 따옴표(`’’`)를 사용

```java
char letter1 = 'a';
char letter2 = 'ab'; // 에러 : 단 하나의 문자만 할당할 수 있습니다.
char letter3 = "a"   // 에러 : 작은 따옴표를 사용해야 합니다.
```

숫자를 문자형 변수에 할당할수도 있다.  변수의 값을 읽어올 때 해당 변수가 저장하고 있는 숫자값을 유니코드로 인식하여 해당 숫자와 일치하는 코드를 가진 문자로 변환해준다.


```java
char letter = 65;
System.out.print(letter); // 출력 결과 : A
```

## 3. 문자열(String)

자바는 String 클래스 타입을 사용해서 문자열을 다룬다. 다른 타입들과 다르게 그 자체로 타입으로 사용될 수 있으며, 연관된 기능들을 묶을 수 있다.

다시말해, String 클래스는 문자열 타입으로 사용되며, 문자열과 관련된 유용한 메서드들을 가지고 있다.

> 학습 목표
- String이 무엇인지 이해한다.
- String을 선언하고 사용하는 법을 이해한다
- String 메서드들을 이해한다.
- StringTokenizer가 무엇인지 이해한다.
- String Builder, Buffer가 무엇인지 이해한다.
{: .prompt-tip }

### 3.1. String 타입의 변수 선언과 할당

기본적으로 String 타입은 큰따옴표("")로 감싸진 문자열을 의미

```java
// 문자열 리터럴을 String 타입의 변수 name에 할당하는 방법
String name1 = "Kim Coding";

// String 클래스의 인스턴스를 생성하는 방법
String name2 = new String("Kim Coding");

// 문자열을 출력해보면 주소값이 아니라 문자열의 내용이 출력됨
System.out.print(name1); // "Kim Coding"
System.out.print(name2); // "Kim Coding"
```

- String 타입의 변수는 `String 변수명;`으로 선언할 수 있다.
- 선언한 변수에 문자열을 할당하는 방법은 두 가지가 있다.
  1. 문자열 리터럴을 할당하는 방법 : `변수 = “문자열”;`
  2. String 클래스의 인스턴스를 생성하여 할당하는 방법 : `변수 = new String(”문자열”);`

문자열 리터럴을 직접 할당하는 방식이든, String 클래스의 인스턴스를 생성하여 할당하는 방법이든 공통적으로 참조 타입의 변수에 할당된다.
`name1`과 `name2`는 **실제 문자열의 내용을 값으로 가지고 있는 것이 아니라, 문자열이 존재하는 메모리 공간 상의 주소값을 저장**

String 타입의 변수를 참조하면 String 클래스의 메서드인 `toString()`이 자동으로 호출되기 때문이다.
`toString()`이 자동으로 호출되면 String 타입의 변수가 저장하고 있는 주소값에 위치한 String 인스턴스의 내용을 문자열로 변환해준다.

```java
// 문자열 리터럴을 String 타입의 변수에 직접 할당하는 방법
String name1 = "Kim Coding";
String name2 = "Kim Coding";

// String 클래스의 인스턴스를 생성하는 방법
String name3 = new String("Kim Coding");
String name4 = new String("Kim Coding");

boolean comparison1 = name1 == "Kim Coding";      // true
boolean comparison2 = name1 == name2;             // true 동일한 문자열 리터럴을 두 변수에 할당하는 경우, 두 변수는 같은 문자열의 참조값을 공유
boolean comparison3 = name1 == name3;             // false
boolean comparison4 = name3 == name4;             // false String 클래스의 인스턴스를 생성하게 되면 문자열의 내용이 같을지라도, 별개의 인스턴스가 따로 생성
boolean comparison5 = name1.equals("Kim Coding"); // true
boolean comparison6 = name1.equals(name3);        // true
boolean comparison7 = name3.equals(name4);        // true

// 등가 비교 연산자는 좌항 == 우항의 형태로 사용좌항의 값과 우항의 값이 일치하는지 검사하여 일치하면 true를, 일치하지 않으면 false를 반환
// equals()메서드는 .앞의 변수가 저장하고 있는 문자열의 내용과 () 안의 문자열의 내용이 같은지 비교하여 같으면 true를 다르면 false를 반환
```

- `comparison1`
  - `name1`은 `Kim Coding`이라는 문자열 리터럴을 직접 할당받았으며, 비교의 대상이 되는 우항 또한 `Kim Coding`이라는 내용이 같은 문자열입니다. 문자열 리터럴은 내용이 같다면 같은 주소값을 가지기 때문에 `true`가 반환됩니다.
- `comparison2`
  - `name1`과 `name2`는 내용이 같은 문자열 리터럴을 직접 할당받은 변수입니다. 따라서 두 변수는 같은 문자열의 참조값을 가지므로, `true`가 반환됩니다.
- `comparison3`
  - `name1`은 문자열 리터럴을 할당 받은 변수이며, `name3`은 String 클래스를 통해 인스턴스를 생성하여 할당받은 변수입니다. String 클래스로 인스턴스를 생성하면 항상 별개의 인스턴스가 생성됩니다. 따라서 `name1`과 `name3`은 다른 주소값을 저장하고 있게 되므로 `false`가 반환됩니다.
- `comparison4`
  - `name3`과 `name4`는 둘 다 String 클래스로 인스턴스를 생성하여 할당받은 변수입니다. String 클래스로 인스턴스를 생성하면 항상 별개의 인스턴스가 생성되므로 두 변수는 서로 다른 주소값을 저장하게 됩니다. 따라서 결과값으로 `false`가 반환됩니다.
- `comparison5`
  - `equals()` 메서드를 활용하여 `name1`과 `“Kim Coding"`의 내용이 같은지 비교하고 있습니다. 이 둘은 참조값도 같고 내용도 같습니다. `equals()` 메서드는 내용이 같은지만을 비교합니다. 따라서 결과값으로 `true`가 반환됩니다.
- `comparison6`
  - `equals()` 메서드를 활용하여 `name1`과 `name3`의 문자열 내용이 같은지 비교하고 있습니다. `name1`과 `name3`은 참조값은 서로 다르지만 내용은 같습니다. 따라서 결과값으로 `true`가 반환됩니다.
- `comparison7`
  - `equals()` 메서드를 활용하여 `name3`과 `name4`의 문자열 내용이 같은지 비교하고 있습니다. `comparison6`의 경우와 마찬가지로, `name3`과 `name4`는 서로 다른 참조값을 가지지만, 이 둘이 가리키고 있는 인스턴스의 내용은 같습니다. 따라서 결과값으로 `true`가 반환됩니다.

### 3.2. String 클래스의 메서드

#### charAt() 메서드

- 해당 문자의 특정 인덱스에 해당하는 문자를 반환
- 문자열의 길이보다 큰 인덱스나 음수를 전달하면, 오류 발생

```java
String str = new String("Java");
System.out.println("문자열 : " + str); // "문자열 : Java"

System.out.println(str.charAt(0)); // 'J'
System.out.println(str.charAt(1)); // 'a'
System.out.println(str.charAt(2)); // 'v'
System.out.println(str.charAt(3)); // 'a'

System.out.println("\ncharAt() 메서드 호출 후 문자열 : " + str);
```

#### compareTo() 메서드

- 해당 문자열을 인수로 전달된 문자열과 사전 편찬 순으로 비교
- 문자열을 비교할 때 대소문자를 구분하여 비교
- 두 문자열이 같다면 0을 반환하며, 해당 문자열이 인수로 전달된 문자열보다 작으면 음수를, 크면 양수를 반환
- 대소문자를 구분하지 않기를 원한다면, `compareToIgnoreCase()` 메서드 사용

```java
String str = new String("abcd");
System.out.println("문자열 : " + str); // 문자열 : abcd
System.out.println(str.compareTo("bcef")); // -1
System.out.println(str.compareTo("abcd") + "\n"); // 0

System.out.println(str.compareTo("Abcd")); // 32
System.out.println(str.compareToIgnoreCase("Abcd")); // 0
System.out.println("compareTo() 메서드 호출 후 문자열 : " + str); // compareTo() 메서드 호출 후 문자열 : abcd
```

#### concat() 메서드

- 해당 문자열의 뒤에 인수로 전달된 문자열을 추가한 새로운 문자열을 반환
- 인수로 전달된 문자열의 길이가 0이면, 해당 문자열을 그대로 반환

```java
String str = new String("Java");
System.out.println("문자열 : " + str); // 문자열 : Java
System.out.println(str.concat("수업")); // Java 수업
System.out.println("concat() 메서드 호출 후 문자열 : " + str); // concat() 메서드 호출 후 문자열 : Java

//contcat은 concatenate의 약자로, 사전적으로 연결한다는 의미
```

#### indexOf() 메서드

- 해당 문자열에서 특정 문자나 문자열이 처음으로 등장하는 위치의 인덱스를 반환
- 해당 문자열에 전달된 문자나 문자열이 포함되어 있지 않으면 -1을 반환

```java
String str = new String("Oracle Java");
System.out.println("문자열 : " + str); // 문자열 : Oracle Java
System.out.println(str.indexOf('o')); // -1
System.out.println(str.indexOf('a')); // 2
System.out.println(str.indexOf("Java")); // 7
System.out.println("indexOf() 메서드 호출 후 원본 문자열 : " + str); // indexOf() 메서드 호출 후 원본 문자열 : Oracle Java
```

#### trim() 메서드

- 해당 문자열의 맨 앞과 맨 뒤에 포함된 모든 공백 문자를 제거

```java
String str = new String(" Java     ");
System.out.println("문자열 : " + str); // 문자열 :  Java
System.out.println(str + '|'); //  Java |
System.out.println(str.trim() + '|'); // Java|
System.out.println("trim() 메서드 호출 후 문자열 : " + str); // trim() 메서드 호출 후 문자열 :  Java
```

**toLowerCase(),  toUpperCase() 메서드**

- `toLowerCase()` 해당 문자열의 모든 문자를 소문자로 변환
- `toUpperCase()` 메서드는 해당 문자열의 모든 문자를 대문자로 변환

```java
String str = new String("Java");
System.out.println("문자열 : " + str); // 문자열 : Java
System.out.println(str.toLowerCase()); // java
System.out.println(str.toUpperCase()); // JAVA
System.out.println("두 메서드 호출 후 문자열 : " + str); // 두 메서드 호출 후 문자열 : Java
```

### 3.2. StringTokenizer

문자열을 우리가 지정한 구분자로 문자열을 쪼개주는 클래스이다.  쪼개어진 문자열을 우리는 토큰(token)이라고 부른다.

StringTokenizer를 사용하기 위해서는 **java.util.StringTokenizer**를 import해야한다.

```java
import java.util.StringTokenizer;

public static void main(String[] args){
	String str = "This is a string example using StringTokenizer"; // This is a string example using StringTokenizer
	StringTokenizer tokenizer = new StringTokenizer(str);
	System.out.println(str);
	System.out.println();

	System.out.println("total tokens:"+tokenizer.countTokens()); // total tokens:7

	while(tokenizer.hasMoreTokens()){
		System.out.println(tokenizer.nextToken());
		/*
			This
			is
			a
			string
			example
			using
			StringTokenizer
		*/
	}
	System.out.println("total tokens:"+tokenizer.countTokens()); // total tokens:0
}
```

- **int countTokens()**
  - 남아있는 token의 개수를 반환
  - 전체 token의 개수가 아닌 현재 남아있는 token 개수
- **boolean hasMoreElements(), boolean hasMoreTokens()**
  - 두 메서드의 성능적인 차이는 없다. 둘다 동일한 값을 반환
  - 메서드는 현재 위치 뒤에 있는 문자열에서 하나 이상의 토큰을 사용할 수 있는 경우 `true`를 반환하고 그렇지 않으면 `false`를 반환
- **Object nextElement(), String nextToken()**
  - 두 가지 메서드는 같은 객체를 반환하는데 반환형은 다르다. nextElement는 Object를, nextToken은 String을 반환


### 3.3. StringBuilder

한번 생성된 String 클래스의 인스턴스는 여러 개의 문자열을 더할 때 매번 새로운 인스턴스를 생성하기 때문에 매우 비효율적이다. 그래서 이 문제를 해결하기 위해 StringBuilder를 사용

```java
public class Main {
    public static void main(String[] args) {
        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append("문자열 ").append("연결");
        String str = stringBuilder.toString();
        System.out.println(stringBuilder); // 문자열 연결
        System.out.println(str); // 문자열 연결
    }
}
```

먼저 StringBuilder의 객체를 생성한 후, `append()`의 인자로 연결하고자 하는 문자열을 넣어서 StringBuilder의 객체를 통해 호출한다.
또한, 문자열을 출력할 때, 그리고 변수에 문자열을 할당할 때에는 `toString()`메서드를 사용하면 됩니다.

### 3.4. StringBuffer

String 클래스의 인스턴스는 한 번 생성되면 그 값을 읽기만 할 수 있고, 변경할 수는 없다. 하지만 StringBuffer 클래스의 인스턴스는 그 값을 변경할 수도 있고, 추가할 수도 있다. 이를 위해 StringBuffer 클래스는 내부적으로 버퍼(buffer)라고 하는 독립적인 공간을 가진다. 버퍼 크기의 기본값은 16개의 문자를 저장할 수 있는 크기이며, 생성자를 통해 그 크기를 별도로 설정할 수도 있다. 하지만 인스턴스 생성 시 사용자가 설정한 크기보다 언제나 16개의 문자를 더 저장할 수 있도록 여유 있는 크기로 생성된다.

덧셈(+) 연산자를 이용해 String 인스턴스의 문자열을 결합하면, 내용이 합쳐진 새로운 String 인스턴스를 생성한다. 참고로 덧셈 연산자를 문자열과 함께 사용하면 자동으로 문자열로 형변환이 이뤄지고 문자열이 결합된다. 따라서 문자열을 많이 결합하면 결합할수록 공간이 낭비될 뿐만 아니라 속도 또한 매우 느려지게 된다. 하지만 StringBuffer 인스턴스를 사용하면 문자열을 바로 추가할 수 있으므로, 공간의 낭비도 없으며 속도도 매우 빨라진다.

#### append()

- 인수로 전달된 값을 문자열로 변환한 후, 해당 문자열의 마지막에 추가
- 이 메서드는 String 클래스의 `concat()` 메서드와 같은 결과를 반환하지만, 내부적인 처리 속도가 훨씬 빠름

```java
StringBuffer str = new StringBuffer("Java");
System.out.println("문자열 : " + str); // 문자열 : Java
System.out.println(str.append(" programming")); // Java programming
System.out.println("append() 메서드 호출 후 문자열 : " + str); // append() 메서드 호출 후 문자열 : Java programming
```

#### capacity()

- StringBuffer 인스턴스의 현재 버퍼 크기를 반환

```java
StringBuffer str01 = new StringBuffer();
StringBuffer str02 = new StringBuffer("Java");
System.out.println(str01.capacity()); // 16
System.out.println(str02.capacity()); // 20
// 길이가 4인 문자열로 StringBuffer 인스턴스를 생성하면, 기본적으로 생성되는 여유 버퍼 크기인 16에 문자의 길이인 4를 더한 총 20개의 문자를 저장할 수 있는 버퍼가 생성
```

#### delete()

- 전달된 인덱스에 해당하는 부분 문자열을 해당 문자열에서 제거합
- `deleteCharAt()` 메서드를 사용하면 특정 위치의 문자 한 개만 제거

```java
StringBuffer str = new StringBuffer("Java Oracle");
System.out.println("문자열 : " + str); // 문자열 : Java Oracle
System.out.println(str.delete(4, 8)); // Javacle
System.out.println(str.deleteCharAt(1)); // Jvacle
System.out.println("deleteCharAt() 메소드 호출 후 문자열 : " + str); // deleteCharAt() 메소드 호출 후 문자열 : Jvacle
```

`delete()` 메서드를 사용하여 해당 문자열에서 인덱스가 4인 위치의 문자부터 7인 위치의 문자까지를 삭제

이처럼 `delete()` 메서드는 첫 번째 매개변수로 전달된 인덱스부터 두 번째 매개변수로 전달된 인덱스 바로 앞의 문자까지를 삭제

#### insert()

- 인수로 전달된 값을 문자열로 변환한 후, 해당 문자열의 지정된 인덱스 위치에 추가
- 전달된 인덱스가 해당 문자열의 길이와 같으면, `append()` 메서드와 같은 결과를 반환

```java
StringBuffer str = new StringBuffer("Java Programming!!");
System.out.println("문자열 : " + str); //문자열 : Java Programming!!
System.out.println(str.insert(4, "Script")); // JavaScript Programming!! (해당 문자열에서 인덱스가 4인 위치부터 두 번째 매개변수로 전달된 문자열을 추가)
System.out.println("insert() 메서드 호출 후 문자열 : " + str); // insert() 메서드 호출 후 문자열 : JavaScript Programming!!
```

## 4. 연산자(Operator)

연산자란, 하나의 값 또는 여러 개의 값을 피연산자로 하여 새로운 값을 만들어내는 기호를 의미

> 학습 목표
- 산술 연산자를 활용할 수 있다.
- 증감 연산자를 활용할 수 있다.
- 복합 대입 연산자를 활용할 수 있다.
- 비교 연산자를 활용할 수 있다.
- 연산자 우선순위를 이해한다.
{: .prompt-tip }

### 4.1. 산술 연산자

산술 연산자는 사칙연산에 사용되는 연산자(`+`, `-`, `*`, `/`)와 나머지 연산자(`%`)를 포함

| 연산자 | 기능 | 예시(int) | 결과값 |
| --- | --- | --- | --- |
| +(덧셈 연산자) | 두 항의 값을 더한 값을 반환합니다. | 7 + 3 | 10 |
| -(뺄셈 연산자) | 좌항의 값에서 우항의 값을 뺀 값을 반환합니다. | 7 - 3 | 4 |
| *(곱셈 연산자) | 두 항의 값을 곱한 값을 반환합니다. | 7 * 3 | 21 |
| /(나눗셈 연산자) | 좌항을 우항으로 나눈 값을 반환합니다. | 7 / 3 | 2 |
| %(나머지 연산자또는 모듈로 연산자) | 좌항의 값을 우항의 값으로 나눈 나머지를 반환합니다. | 7 % 3 | 1 |

```java
int num1 = 1;
int num2 = num1 + 2; // num2 -> 3
int num3 = num2 - 1; // num3 -> 2
int num4 = num3 * 3; // num4 -> 9
int num5 = num4 / 2; // num5 -> 4
int num6 = num5 % 3; // num6 -> 1
```

나눗셈 연산자와 나머지 연산자를 사용할 때에는 우항에 0이 위치할 수 없다. (어떤 수를 0으로 나눌 수 없음)

```java
int    num1 = 9 / 0;   // 에러
double num2 = 9.0 / 0; // Infinity

int    num3 = 9 % 0;   // 에러
double num4 = 9.0 % 0; // 에러
```

나눗셈 연산자를 사용할 때, 좌항과 우항이 모두 `int`형이면 그 결과도 `int`형이기 때문에 소수점 이하의 값은 버려지고, 오직 몫만 결과로 반환

반면, 좌항이나 우항 중 하나라도 실수 타입의 값이 존재한다면, 실수 타입이 아닌 값도 실수 타입으로 자동으로 형변환되어 계산되며, 결과적으로 실수 간의 나눗셈 연산이 되어 소수점이 버려지지 않은 온전한 값이 결과값으로 반환

```java
double num1 = 9 / 2;   // 4.0
int    num2 = 9 / 2;   // 4
double num3 = 9.0 / 2; // 4.5
```

### 증감연산자

변수의 값을 1씩 증가시키거나 감소시키는 연산자

코드를 작성하다보면, 어떤 정수 타입 변수가 가진 값을 증가시키거나 감소시켜야 하는 경우가 있다. 예를 들어, 1이라는 값을 할당받아 저장하고 있는 변수 `num1`의 값을 1 증가시켜야 한다면, 그리고 1이라는 값을 할당받아 저장하고 있는 변수 `num2`의 값을 1 감소시켜야 한다면 아래와 같은 코드를 작성할 수 있다.

```java
num1 = num1 + 1; // num1의 값은 2가 됩니다.
num2 = num2 - 1; // num2의 값은 0이 됩니다.

// 줄여서 작성 가능
num1++; // num1 = num1 + 1;과 같습니다.
++num1; // num1 = num1 + 1;과 같습니다.

num2--; // num2 = num2 - 1;과 같습니다.
--num2; // num2 = num2 - 1;과 같습니다.
```

주의해야 할 점은 연산 순서가 증감연산자의 위치에 따라 달라질 수 있다.

- 전위형 증감연산자 : 증감 연산을 먼저 수행한 후, 그 결과값을 적용
- 후위형 증감연산자 : 기존의 값을 먼저 적용시키고 그 다음에 증감 연산을 수행

```java
int num1 = 1;
int prefix = ++num1; // num1의 값이 1만큼 먼저 증가된 다음 그 결과값이 prefix에 할당 -> num1의 값은 2, prefix의 값도 2

int num2 = 1;
int postfix = num2++; // num2의 값이 먼저 postfix에 할당된 다음에 num2의 값이 1 증가 -> num2의 값은 2, postfix의 값은 1
```

### 복합 대입 연산자

대입 연산자는 사칙 연산자와 함께 조합하여 복합 대입 연산자로 활용

```java
// 1씩 증가시키거나 감소시키고자 하는 상황에서는 증감 연산자를 사용
num1 = num1 + 1;
num2 = num2 - 1;

// 1이 아니라 2 혹은 3씩 증가시키거나 감소시키고 싶을 때에는 증감 연산자를 사용할 수 없음
num1 = num1 + 2;
num2 = num2 - 2;

// 복합 대입 연산자를 사용하여 연산을 간략하게 표현
num1 += 2;
num2 -= 2;

// 모든 사칙 연산자 및 나머지 연산자와 대입 연산자를 결합해서 복합 대입 연산자로 사용
// num1~5의 값을 모두 10이라고 한다면,
num1 += 3; // num1 -> 13
num2 -= 3; // num2 -> 7
num3 *= 3; // num3 -> 30
num4 /= 3; // num4 -> 3
num5 %= 3; // num5 -> 1
```

## 4.2. **비교 연산자**

비교 연산자는 `boolean` 타입으로 평가될 수 있는 조건식에 사용되며, 크게 대소 비교(`>`, `<`, `<=`, `>=`)연산자와 등가 비교(`==`, `!=`) 연산자로 분류

### **대소 비교 연산자**

- `boolean`을 제외한 나머지 기본 타입에 모두 사용 가능
- 이항 비교만 가능
- “`x`가 1보다 크고 5보다 작다”를 표현할 때, `1 < x < 5`가 아니라, `1 < x && x < 5`와 같이 논리 연산자를 사용해 작성해주어야 함

| 대소 비교 연산자 | 결과 |
| --- | --- |
| 5 > 3 | true |
| 5 <= 5 | true |
| 3 > 2 | true |
| 2 >= 3 | false |

### **등가 비교 연산자**

- 등가 비교 연산자는 모든 타입에 사용할 수 있는 연산자로, 두 항의 값이 동등한지의 여부를 판단할 때 사용
- 기본 타입과 참조 타입 간에는 등가 비교 연산자를 사용할 수 없다. (기본 타입의 값끼리, 혹은 참조 타입의 값끼리만 등가 비교 연산자를 사용)
- 값이 동등하면 `true`를, 그렇지 않으면 `false`를 반환

| 등가 비교 연산자 | 결과 |
| --- | --- |
| 5 == 3 | false |
| 5 == 5 | true |
| 3 != 2 | true |
| 3 != 3 | false |

## 4.3. 논리 연산자

논리 연산자는 AND 연산자 `&&`, OR 연산자 `||`, NOT 연산자 `!`를 포함하며, 공통적으로 `boolean` 타입을 반환

- AND 연산자(`&&`): 피연산자 두 개가 모두 `true`일 때 `true`를 반환하며, 피연산자 두 개 중 하나라도 `true`가 아니면 `false`를 반환
- OR 연산자(`||`): 피연산자 두 개 중 단 하나라도 `true`면 `true`를 반환하며, 피연산자가 모두 `false`인 경우에만 `false`를 반환

NOT 연산자(!)는 `true`와 `false`를 반대로 바꾸는 연산자

```java
// 아래의 비교 연산 결과는 모두 true입니다.
!true == false
!false == true
!!true == true
```

## 4.4. 연산자 우선순위

| 우선순위 | 연산자 | 내용 |
| --- | -- | --- |
| 1 | (),[] | 괄호 / 대괄호 |
| 2 | !, ~, ++, -- | 부정/ 증감 연산자 |
| 3 | *, /, % | 곱셈 / 나눗셈 연산자 |
| 4 | <, <=, >, >= | 대소 비교 연산자 |
| 5 | && | AND 연산자 |
| 6 | &#124; &#124; | OR 연산자 |
| 7 | ? : | 조건 연산자 |
| 8 | =, +=, -=, /=, %= | 대입/할당 연산자 |

```java
// (참 또는 거짓) ? 참일 때 결과 : 거짓일 때 결과
int num = (1 + 2 == 3 && 4 + 1 * 2 == 6) ? 3 + 4 : 5 + 6;
System.out.println(num);
```

1) `*` 곱셈 연산자가 수행됩니다.

```java
int num = (1 + 2 == 3 && 4 + 2 == 6) ? 3 + 4 : 5 + 6;
```

2) `+` 덧셈 연산자가 수행됩니다.

```java
int num = (3 == 3 && 6 == 6) ? 7 : 11;
```

3) `==` 등가 연산자가 수행됩니다.

```java
int num = (true && true) ? 7 : 11;
```

4) `&&` AND 연산자가 수행됩니다.

```java
int num = true ? 7 : 11;
```

5) `? :` 조건 연산자가 수행됩니다.

```java
int num = 7;
```

6) `=` 대입 연산자가 수행되어 7이 출력됩니다.

괄호를 먼저 연산하고, 곱셈, 나눗셈이 덧셈, 뺄셈보다 먼저 연산

## 5. **콘솔 입출력(I/O)**
개의 값을 피연산자로 하여 새로운 값을 만들어내는 기호를 의미

> 학습 목표
- 다음의 콘솔 출력 메서드들의 차이를 이해하고, 이를 활용할 수 있다.
  - System.out.print()
  - System.out.println()
  - System.out.printf()
- Scanner를 활용하여 문자열 데이터를 입력받을 수 있다.
{: .prompt-tip }

### 5.1. 콘솔 출력

콘솔에 값을 출력하기 위해서는 `System.out.print()`, `System.out.println()`, `System.out.printf()` 메서드를 활용

**출력하기 : System.out.print()**

`System.out.print()` 메서드는 소괄호 안의 내용을 단순히 출력하기만 하고, 줄바꿈을 하지 않는다.

```java
System.out.print("Hello JAVA");
System.out.print("Kim" + "Coding");
System.out.print(3+6);
System.out.print(2022 + "year");
```

`System.out.print(”Hello Java”)`를 실행하면 소괄호 안의 `“Hello Java”`가 출력되고 커서는 출력된 “Hello Java”뒤로 이동합니다.

**출력하고 줄 바꾸기 : System.out.println()**

`System.out.println()` 메서드는 소괄호 안의 내용을 콘솔에 출력하고 줄바꿈

`print`뒤에 붙은 `ln`은 line을 의미

```java
System.out.println("Hello JAVA");
System.out.println("Kim" + "Coding");
System.out.println(3+6);
System.out.println(2022 + "year");
```

`System.out.println(”Kim Coding")`을 실행하면 소괄호 안의 `”Kim Coding"`이 출력되고 커서는 다음 줄로 이동

**형식대로 출력하기 System.out.printf()**

`System.out.printf()`는 지시자(specifier, 형식 지정자)를 이용해 변수의 값을 여러 형식으로 출력해주는 메서드

이름 그대로 값을 어떤 형식으로 출력할 것인지를 지정하기 위해 사용 `f`는 formatted의 약자

지시자는 실제로 출력되는 값이 아니며, 값을 변환해 자신의 위치에 출력해주는 기능

```java
System.out.printf("%s%n", "Hello JAVA"); // 줄바꿈이 됩니다.
System.out.printf("%s%n", "Kim" + "Coding");
System.out.printf("%d%n", 3+6);
System.out.printf("지금은 %s입니다", 2022 + "year"); // 자동 타입 변환이 일어납니다.
System.out.printf("나는 %c%s입니다", '김', "코딩"); //여러 개의 인자를 넣을 수 있습니다.
```

### 5.2. 콘솔 입력

```java
import java.util.Scanner;                 // Scanner 클래스를 가져옵니다.

Scanner scanner = new Scanner(System.in); // Scanner 클래스의 인스턴스를 생성합니다.
String inputValue = scanner.nextLine();   // 입력한 내용이 inputValue에 저장됩니다.

System.out.println(inputValue);           // 입력한 문자열이 출력됩니다.
```

1. `import java.util.Scanner;`

   데이터를 입력받는 기능을 작은 프로그램으로 만들어둔 것이 Scanner이다. 이 Scanner는 java.util이라는 위치에 저장되어져 있는데, Scanner를 사용하려면 Scanner를 불러와야 한다. `import java.util.Scanner;`

2. `Scanner scanner = new Scanner(System.in);`

   위에서 불러온 Scanner는 클래스이다. 데이터 입력 기능을 사용하려면 Scanner 클래스를 통해 객체를 먼저 만들어야 한다.

   클래스를 통해 객체를 만들어 낼 때에는 `new` 연산자를 사용하며, 그 결과물로 만들어진 객체를 인스턴스라고 한다. 이렇게 클래스에 `new` 연산자를 적용하여 인스턴스를 만드는 것을 ‘클래스를 인스턴스화한다'고 표현한다.

   위의 코드는 불러온 Scanner 클래스를 `new` 연산자를 통해 인스턴스를 생성하고, 생성된 인스턴스를 변수 `scanner`에 할당하는 코드입니다.

3. `String inputValue = scanner.nextLine();`

   위에서 Scanner 클래스를 인스턴스화한 `scanner`에는 `nextLine()`이라는 메서드가 존재한다. 이 메서드는 콘솔을 통해 문자열 데이터를 입력 받는 기능을 수행한다. 즉 `scanner.nextLine()`은 문자열을 입력받기 위한 코드이며, 입력받은 문자열은 `inputValue`라는 변수에 할당되어 저장된다.


`scanner`에는 문자열을 입력받는 `nextLine()`뿐만 아니라, 정수형을 입력받을 수 있는 `nextInt()`, 실수형을 입력받을 수 있는 `nextFloat()`등의 메서드들도 존재한다.




## Reference

[JDK 18 Documentation - Home](https://docs.oracle.com/en/java/javase/18/)

[예약어(reserved word)](https://www.w3schools.com/java/java_ref_keywords.asp)

[Naming Conventions](https://www.oracle.com/java/technologies/javase/codeconventions-namingconventions.html)

[Understanding toString() method - javatpoint](https://www.javatpoint.com/understanding-toString()-method)

[StringBuffer 클래스의 API 문서](https://docs.oracle.com/javase/7/docs/api/java/lang/StringBuffer.html)
