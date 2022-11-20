---
title: 웹개발 기초
author: keumbi
date: 2022-08-22 21:20:00 +0900
categories: [How to...]
tags: [week2, development, computer, programming, web]
---


## Overview
프로그램은 소프트웨어 또는 애플리케이션이라고도 불리는데, 어떤 애플리케이션이 웹을 기반으로 구동되면 그 애플리케이션을 웹 애플리케이션(web application)
이라고 합니다.  웹 애플리케이션의 핵심 구성 요소 중 하나인 서버 애플리케이션을 개발하기 위한 기술을 학습하게 됩니다. 컴퓨터, 프로그래밍, 그리고 웹에 대한 기초적인 이해와 앞으로 학습에 사용할 개발 도구들을 세팅하는 것으로부터 시작됩니다.


## 1. 컴퓨터와 프로그래밍의 이해

**컴퓨터: 입력 받은 데이터를 정해진 규칙대로 처리해서 처리 결과를 저장하고 출력하는 전자 장치**

- 소프트웨어: 하드웨어의 동작을 지시하고 제어하는 명령어의 집합
- 하드웨어: 컴퓨터를 구성하는 기계적 장치

### 1.1. 소프트웨어

물리적인 형태가 존재하지 않는 컴퓨터의 구성 요소, 하드웨어의 동작을 지시하는 명령어의 집합

- **시스템 소프트웨어(System Software)**

  응용 소프트웨어를 실행하기 위한 플랫폼 역할을 수행, 하드웨어와 직접적으로 소통하며 하드웨어 장치들이 제대로 동작할 수 있도록 해줌

  - **응용 소프트웨어의 실행 환경**
    - Ex. Mac, Windows, Linux와 같은 운영체제 및 Node.js, JRE와 같은 런타임 환경
  - **하드웨어 장치를 관리**
    - Ex. 키보드 드라이버, 마우스 드라이버, USB 드라이버와 같은 각종 장치 드라이버들
- **응용 소프트웨어(Application Software)**
  시스템 소프트웨어를 제외한 모든 소프트웨어, 줄여서 애플리케이션 및 앱이라고도 하며, 일반적으로 프로그램이라고도 불린다.

### 1.2. 하드웨어

컴퓨터를 구성하는 기계적 장치들의 집합, 컴퓨터의 물리적인 장치이고, 각 장치는 시스템 버스로 연결됨

중앙처리장치, 기억장치, 입력장치, 출력장치, 시스템 버스

#### 중앙처리장치 (Central Processing Unit, CPU)

프로그램의 실행과 데이터 처리를 담당하는 컴퓨터의 핵심 장치로, 프로세서라고도 한다.  제어장치, 연산장치, 레지스터로 구성되며, 각 요소의 동작이 어우러져 CPU의 기능을 수행한다.

- **제어장치**
  - CPU의 모든 동작과 데이터 흐름을 통제하고 관리
  - 운영체제와 소통하며 컴퓨터의 자원을 관리
- **연산장치**
  - 프로그램에 기술되어져 있는 명령어를 수행
  - 코드를 실질적으로 실행시키는 장치
- **레지스터**
  - CPU 내에 존재하는 작고 빠른 기억 장치
  - 연산장치의 동작에 필요한 데이터들을 임시적으로 보관하고 제공

#### 기억장치 (Memory Device)

- **보조기억장치(장기적으로 데이터를 저장하는 장치)**
  - 컴퓨터에게 필요한 모든 정보를 반영구적으로 저장
  - 큰 용량의 데이터를 저장할 수 있지만, 데이터를 읽고 쓰는 속도가 느리다
  - CPU의 연산 속도가 빠른 반면, 보조기억장치는 느리기 때문에 CPU는 보조기억장치와 직접적으로 소통 안 함
  - Ex. SSD(Solid State Drive), HDD (Hard Disk Drive)
- **주기억장치(단기적으로 데이터를 저장하는 장치)**
  - 컴퓨터가 프로그램을 수행하는 동안 필요한 모든 데이터들을 저장
  - 큰 용량의 데이터를 저장할 수 없지만, 데이터를 읽고 쓰는 속도가 빠르다
  - CPU의 연산 속도를 어느 정도 따라 잡을 수 있을 정도로 빠르기 때문에 CPU는 주기억장치와 직접적으로 소통
  - Ex. RAM(Random Access Memory), ROM (Read Only Memory)


💡  **캐시 메모리 (Cache Memory)**
CPU가 한 번 사용한 데이터와 관련된 데이터 중, 재사용 가능성이 높은 데이터를 주기억장치로부터 미리 불러와서 대기 시킴

💡  **기억장치의 계층구조**
CPU에 직접 연결된 주기억장치는 기억 용량이 작고, 속도가 빠른 반면  비용은 증가하고, 보조기억장치는 속도는 느리지만, 가격이 저렴하고, 기억 용량이 큼

| 접근 시간 / 기억 용량 | 기억장치                                              | 접근 속도 / 비트 당 가격 |
|---------------|---------------------------------------------------|-----------------|
| ↓ Low         | CPU 내의 레지스터: Register                             | ↑ Hight         |
| ↓             | 캐시기억장치(Cache Memory): Static RAM                  | ↑               |
| ↓             | 주기억장치(Main Memory): Dynamic Ram                   | ↑               |
| ↓ Hight       | 보조기억장치(Secondary Memory): HDD, FDD, Magnetic Tape | ↑ Low           |


#### 입력장치 (Input Device)

사용자로부터 컴퓨터 내부로 데이터를 입력 받는 장치 예)키보드, 마우스, 마이크, 트랙패드 등…

#### 출력장치 (Output Device)

컴퓨터 내부로부터 사용자에게 사람이 감각할 수 있는 형태로 데이터를 출력해주는 장치 예)모니터, 스피커, 프린터 등…

#### 시스템 버스 (System Bus)

CPU를 포함한 각 하드웨어 장치 간의 통로, 각 하드웨어 장치를 물리적으로 연결한 전선을 의미하므로 시스템 버스 또한 하드웨어에 포함됨

- **데이터 버스:** 하드웨어 간에 데이터를 전달하는 통로
- **주소 버스:** 데이터가 어디에 도착해야 하는지에 대한 정보를 전달하는 통로
- **제어 버스:** CPU의 제어장치가 생성한 제어 신호를 다른 장치로 전달하는 통로

### 1.3. 프로그래밍의 이해

#### 프로그래밍

프로그램을 만드는 과정으로서, 특정 목적을 달성하기 위해 설계된 알고리즘을 프로그래밍 언어를 사용하여 코드로 작성하는 과정

#### 프로그래밍 언어

컴퓨터의 언어와 사람의 언어를 매개해주는 언어

Hello Wolrd! 기계어 코드

```java
b8 21 0a 00 00 a3 0c 10 00 06 b8 6f 72 6c 64 a3 08 10 00 06 b8 6f 2c 20 57
a3 04 10 00 06 b8 48 65 6c 6c a3 00 10 00 06 b9 00 10 00 06 ba 10 00 00 00
bb 01 00 00 00 b8 04 00 00 00 cd 80 b8 01 00 00 00 cd 80
```

Hello Wolrd! 프로그래밍 언어 코드

```java
System.out.println("Hello World!");
```

#### 컴파일

프로그래밍 언어로 작성된 소스 코드를 컴퓨터가 이해할 수 있는 기계어 코드로 번역하는 과정

#### 빌드

작성한 소스 코드를 실행할 수 있는 산출물로 변환 시키는 과정

#### 통합개발환경 (Integrated Development Environment, IDE)

코드를 작성할 때 사용하는 프로그램으로, 프로그래밍에 필요한 모든 작업을 하나의 프로그램 안에서 처리할 수 있도록 만들어진 프로그램

IDE를 사용하면 단순히 코드를 작성하고 편집하는 것뿐만 아니라, 디버깅, 빌드 등의 작업을 하나의 IDE 안에서 할 수 있다.

예) Visual Studio Code, IntelliJ, Eclipse 등…

## 2. 웹 클라이언트와 웹서버

### 2.1. 클라이언트-서버 아키텍처 Client Server Architecture (2 Tier Architecture)

리소스가 존재하는 곳과 리소스를 사용하는 앱을 분리시킨 것

![[https://opentutorials.org/course/3084/18890](https://opentutorials.org/course/3084/18890)](https://s3-ap-northeast-2.amazonaws.com/opentutorials-user-file/module/3135/7752.jpeg)

[https://opentutorials.org/course/3084/18890](https://opentutorials.org/course/3084/18890)

**클라이언트:** 리소스를 사용하는 앱 (웹사이트, 스마트폰/태블릿용 앱, 데스트탑 앱)

**서버:** 리소스를 제공 하는 곳 (웹 서버, 파일 서버, 메일 서버, 데이터베이스 서버)

클라이언트와 서버는 요청과 응답을 주고받는 관계, 클라이언트-서버 아키텍처에서는 요청이 선행되고 그 후에 응답이 온다.

### 2.2. 3-Tier 아키텍처

2티어 아키텍처에 데이터베이스가 추가된 형태

**클라이언트**

**서버**

**데이터베이스:** 리소스 저장 공간

## 3. 개발 환경 세팅

WSL2: Windows Subsystem for Linux 2의 약자로, Windows에서 리눅스 터미널을 실행할 수 있게 해주는 프로그램

### WSL2설치

Microsoft Store에서 Windows Terminal을 검색하여 다운로드

`dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`

`dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`

'x64 머신용 최신 WSL2 Linux 커널 업데이트 패키지'를 다운로드 받고 실행

`wsl --set-default-version 2`

### 우분투 리눅스 설치

Microsoft Store에서 ubuntu를 검색한 후, 다운로드

사용자의 이름과 비밀번호를 입력

### JDK설치

[Zulu OpenJDK 다운로드 페이지](https://www.azul.com/downloads/?version=java-11-lts&os=windows&architecture=x86-64-bit&package=jdk)에 접속 다운로드

“windows + R” 키를 눌러 실행 창을 열고 cmd를 입력해 명령 프롬프트를 실행

명령 프롬프트 창에 java를 입력 결과 확인

### IntelliJ 설치

’IntelliJ’를 검색하여 다운로드 페이지로 이동

### JetBrains Toolbox 설치

IDE를 손쉽게 설치할 수 있게 해주고, 설치한 IDE의 버전을 관리해주는 프로그램

1.  [JetBrains Toolbox download](https://www.jetbrains.com/lp/toolbox/)로 접속하여 'Download the App'을누른다.
2. 설치가 완료되면 'JetBrains Toolbox 실행하기'를 체크해주고 '마침'을 누른다.

### 환경변수 설정


1. 윈도우에서 환경 변수를 검색하여 '시스템 환경 변수 편집'을 열어주세요.
2. 환경 변수를 눌러줍니다.
3. 시스템 변수 탭에서 새로 만들기를 클릭하고, 값을 입력해줍니다.
  * 변수 이름 : `JAVA_HOME`
  * 변수 값 : `C:₩Program Files₩Zulu₩zulu-11`
  * 시스템 변수에 방금 설정한 환경 변수가 제대로 만들어졌는지 확인
4. 시스템 변수에서 Path를 찾아 클릭하고, 편집을 눌러줍니다.
5. 새로만들기를 누른 다음, 아래의 경로를 추가해주시고, 확인을 눌러주세요.
  * `%JAVA_HOME%₩bin`
6. 방금 전 JAVA_HOME을 만들었던 것과 동일한 방법으로 아래의 환경 변수를 추가해주세요.
   * 변수 이름 : CLASSPATH
   * 변수 값 : `%JAVA_HOME%₩lib`
7. 환경 변수 설정이 제대로 완료되었는지 확인합니다.
   * 작업표시줄의 검색바에서 cmd를 검색하여 명령 프롬프트를 실행한 후, path를 입력하고 엔터를 눌러줌

## 4. Intellij와 친해지기

인텔리제이는 자바를 사용하여 개발하는 데에 있어 많이 사용되는 IDE입니다

### [⌥⏎ or Alt + Enter](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#Alt_Enter)

문제에 대한 수정 제안 목록이 표시

### [F2](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#F2)

오류와 경고 사이를 이동할 때 F2를 사용하면 다음 오류,경고 또는 제안으로 이동

### [⌘1 or Alt+1](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#%E2%8C%981_or_Alt1)

에디터에서 타이핑 중 사용하면 프로젝트 창이 열리고 포커스가 위치함. 방향키를 이용하여 탐색하거나 입력하여 검색 가능

### [Esc](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#Esc)

에디터에 다시 포커스가 위치하게 하려면 사용. 열린 도구창과 상관없이 에디터에 다시 포커스가 위치하게 됨

### [⌘E or Ctrl+E](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#%E2%8C%98E_or_CtrlE)

최근 실행했던 파일을 확인할 수 있는 파일상자가 표시됨. 방향키로 이동할 수 있고, 키보드를 입력하여 검색도 가능

### [⌘B or Ctrl+B](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#%E2%8C%98B_or_CtrlB)

코드 안에서 다른 코드로 이동하고 싶을 경우 Ctrl+B 클릭 시 해당 코스가 열림

### [Alt+F7](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#AltF7)

어떤 항목이 사용된 모든 곳이 표시됨, 예를 들어 인터페이스 이름 위에 Alt+F7을 누르면 이 인터페이스를 구현한 필드 또는 클래스가 사용된 모든 곳이 검색 창에 표시됨

### [Ctrl Ctrl](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#Ctrl_Ctrl)

어떤 항목이든 실행할 수 있는 Run Anything 창이 열림

### [⌥↑ / ⌥↓ or Ctrl + W / Shift + Ctrl + W](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#%E2%8C%A5%E2%86%91_%E2%8C%A5%E2%86%93_or_Ctrl_W_Shift_Ctrl_W)

커서 근처의 코드 선택 영역을 확대하거나 축소 할 수 있음

### [⌘/ or Ctrl + /](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#%E2%8C%98_or_Ctrl)

해당 코드줄이 주석 처리 됨, 이미 주석 처리된 부분은 주석 해제됨

### [⇧⌘⏎ or Shift+Ctrl+Enter](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#%E2%87%A7%E2%8C%98%E2%8F%8E_or_ShiftCtrlEnter)

현재 구문 완성, 코딩할 때 매우 유용함, String str = "11" 까지 입력 후 Shift + Ctrl + Enter 입력 시 세미콜론이 추가됨.

for 루프 작성시에도 유용

### [⌥⌘L or Ctrl+Alt+L](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#%E2%8C%A5%E2%8C%98L_or_CtrlAltL)

소스 코드 자동 포맷팅 (줄맞춤 등)

### [⌃T or Shift+Ctrl+Alt+T](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#%E2%8C%83T_or_ShiftCtrlAltT)

리팩토링 옵션이 표시됨, 예를 들어 소스상에 변수를 변경하고자 할 경우 해당 변수에 커서를 두고 Shift+Ctrl+Alt+T 입력 후 Rename.. 시 해당 변수를 사용하고 있는 모든 소스가 자동으로 rename 처리 됨

### [⇧⌘A or Shift+Ctrl+A](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#%E2%87%A7%E2%8C%98A_or_ShiftCtrlA)

인텔리제이의 모든 액션을 검색할 수 있는 Find Action 창 호출

### [Shift shift](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#Shift_shift)

Search Everywhere(전체 검색) 모든 항목을 검색 할 수 있는 검색 상자가 열림

### [More Information](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/#More_Information)


## Reference
[Top 15 intellij idea shortcuts](https://blog.jetbrains.com/idea/2020/03/top-15-intellij-idea-shortcuts/)


