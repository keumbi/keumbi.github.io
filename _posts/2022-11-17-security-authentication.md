---
title: 인증 / 보안 기초
author: keumbi
date: 2022-11-17 23:20:00 +0900
categories: [Framework, Spring]
tags: [week14, https, hashing, cookie, session, web application security ]
mermaid: true
---

## Overview
웹 사이트에 보안은 굉장히 중요한 요소입니다. 보안이 제대로 되어 있지 않다면 여러분들의 개인정보가 악의적인 곳에 유출될 가능성이 있습니다.
Spring Framework에서는 Spring Security를 통해 보안 관련 기능을 편리하게 지원하고 있습니다.
Spring Security를 이용해 인증과 보안을 구현하기에 앞서, 인증과 보안의 기초가 되는 개념들에 대해 알아보겠습니다.

> 학습목표
- 암호화와 hashing, salting 등의 개념을 이해할 수 있다.
- HTTP와 HTTPS의 차이점을 이해할 수 있다.
- 권한 부여(Authorization)와 인증(Authentication)에 대해 이해할 수 있다.
- 쿠키의 작동 원리를 이해할 수 있다.
- 클라이언트, 서버, 데이터베이스의 전체 동작을 이해할 수 있다.
- 서비스의 보안과 관련된 방법을 알아보고 원리 및 장점 및 단점을 이해할 수 있다.
{: .prompt-tip }

## 1. HTTPS

`HTTPS`는 **H**yper **T**ext **T**ransfer **P**rotocol **S**ecure Socket layer 의 약자입니다. HTTP over SSL(TLS), HTTP over Secure라고 부르기도 합니다. `HTTPS`는 `HTTP` 요청을 `SSL` 혹은 `TLS`라는 알고리즘을 이용해, `HTTP` 통신을 하는 과정에서 데이터를 암호화하여 전송하는 방법입니다. `HTTPS`는 다음을 목적으로 사용합니다.

**비대칭키 방식을 통해 대칭키를 주고받고, 대칭키 방식을 통해 클라이언트와 서버가 데이터를 주고받는다.**

- HTTP 프로토콜 내용을 암호화 하는 것을 의미 한다.
- 인증서 발급 기관에서 발급된 인증서를 통해 검증 절차를 진행한다.
- HTTPS에서는 비대칭키 암호화를 이용한다.

### 1.1. 암호화(Encryption)

**암호화는 일련의 정보를 임의의 방식을 사용하여 다른 형태로 변환하여, 해당 방식에 대한 정보를 소유한 사람을 제외하고 이해할 수 없도록 '알고리즘'을 이용해 정보를 관리하는 과정을 말합니다.**

클라이언트와 서버가 데이터를 암호화하여 통신할 때, 대칭키 방식과 비대칭키 방식을 혼용하여 사용합니다.

- 대칭키: 클라이언트와 서버 양쪽이 공통의 비밀 키를 공유하여 데이터를 암호화 및 복호화하는 것(키 한 개로 암 복호)
- 비대칭키: 클라이언트와 서버 각각 공개키와 비밀키를 가지고 상대가 나의 공개키로 암호화한 데이터를 개인이 가진 비밀키로 복호화하는 것(암호/복호 키가 다름)

클라이언트와 서버가 데이터를 주고, 받을 때는 대칭키를 사용합니다.
비대칭키의 알고리즘 복잡도가 훨씬 복잡하기 때문에 통신 시 컴퓨터의 부담을 덜기 위해서 대칭키를 사용합니다.
하지만 대칭키를 이용한 통신은 위험할 수 있습니다.
대칭키를 주고받는 과정에서 대칭키를 탈취당한다면 모든 데이터가 복호화될 수 있기 때문입니다.

위 문제를 해결하기 위한 비대칭키 방식입니다.
비대칭키 방식을 통해서 대칭키를 주고받는다면 대칭키를 탈취당하더라도 개인이 가진 개인키로만 복호화할 수 있기 때문에, 외부로부터 데이터를 안전하게 지킬 수 있습니다.

### 1.2. 인증서

HTTPS의 특징은 클라이언트가 서버로부터 응답을 전달받을 때, 함께 전달된 인증서를 확인할 수 있다는 점이다. 인증서는 서버의 신원을 보증하여, 사용자가 접속한 사이트가 가짜인지 진짜인지를 구분해줍니다.


**Certificate Authority**

서버의 신원을 보증해주며, 인증서를 발급해주는 기관을 Certificate Authority, 줄여서 CA라고 부릅니다. CA들은 서버의 공개키와 정보를 CA의 비밀키로 암호화하여 인증서를 발급한다.

인증서가 CA의 비밀키로 암호화되어 있으므로 CA의 공개키로 복호화 가능하다. 따라서 해당 CA에서 발급한 인증서라는 것을 보증할 수 있다. 만약 인증서가 위조되었다면 CA의 공개키로 서버의 인증서를 복호화할 수 없다.


**CA에서 발급한 인증서라는 것을 보증하는 과정**

1. 서버가 클라이언트에게 인증서를 전달한다.
2. 클라이언트 측의 OS 또는 브라우저에 미리 내장되어 있던 CA 리스트를 확인한다.
3. 만약 CA에서 발급한 인증서가 아니라면 서버와의 연결이 안전하지 않다는 경고창을 띄운다.
4. CA에서 발급한 인증서가 맞는다면 브라우저에 제공된 해당 CA 기관의 공개키로 서버 인증서를 복호화한다.

**인증서 사용 시 장점**

중간자 공격을 감지하여 보안 위협으로부터 사용자의 데이터를 보호할 수 있다.
브라우저들은 경고창을 띄우면서 CA가 인증서를 발급한 안전한 서버를 사용하도록 유도할 수 있다.

서버와 클라이언트 간의 CA를 통해 서버를 인증하는 과정과 데이터를 암호화하는 과정을 아우른 프로토콜을 SSL 또는 TLS이라고 말한다. (*SSL과 TLS는 사실상 동일한 규약을 뜻하며 SSL이 표준화되며 바뀐 이름이 TLS이다.)



## 2. Hashing

입력받은 데이터를 고정된 길이의 데이터로 변환하여 이전 데이터를 알아볼 수 없게 만든다.

### 2.1. 해싱이란?

어떠한 문자열에 `임의의 연산`을 적용하여 다른 문자열로 변환하는 것입니다.
1. 모든 값에 대해 해시값을 계산하는 데 오래 걸리지 않아야 합니다.
2. 최대한 해시 값을 피해야 하며, 모든 값은 고유한 해시값을 가져야 합니다.
3. 아주 작은 단위의 변경이라도 완전히 다른 해시 값을 가져야 합니다.

### 2.2. 해싱 사용 과정

비밀번호를 이용한 인증 요청(eg. 로그인)이 올 때마다 그 알고리즘을 통해서 암호화를 시켜주고,
DB에 저장되어있는 값을 확인한 후,
맞으면 요청한 데이터를 가져와서 클라이언트에게 반환하는 과정을 가지게 될 것입니다.

### 2.3. Salt

암호화 해야 하는 값에 어떤 '별도의 값'을 추가하여 결과를 변형시킵니다.

**Salt 사용 시 주의사항**

1. 솔트는 유저와 패스워드별로 유일한 값을 가져야 합니다.
2. 사용자 계정을 생성할 때와 비밀번호를 변경할 때마다 새로운 임의의 솔트를 사용해서 해싱해야 합니다.
3. 솔트는 절대 재사용 하지 말아야 합니다.
4. 솔트는 DB의 유저 테이블에 같이 저장되어야 합니다.

### 2.4. 해싱 알고리즘

- SHA-1, SHA256, SHA512, etc. 숫자가 클수록 복잡한 연산으로 인해 복호화가 어려습니다.
- input -> output 항상 동일한 순수 함수입니다.
- 해싱된 값(다이제스트)은 사실상 복호화 불가능 합니다.

**높은 알고리즘을 사용할 경우 그만큼 연산 비용이 올라가기 때문에 서비스에 적합한 알고리즘을 사용하는것이 좋습니다.**

```mermaid
flowchart LR
A[Salt] --- | plus | B[Password]
B --> C(Hash) --> D([Digest])
```



## 3. Cookie

 HTTP 특징인 무상태, 비연결성을 보완하기 위해 서버가 웹 브라우저에 전송하는 데이터 조각으로서 데이터 조각들을 저장해 놓았다가 서버에 요청할 때 저장된 쿠키 데이터들을 함께 전송하여 사용하는 방식입니다.

서버에서 클라이언트 데이터를 저장하는 방법의 하나이고, 서버가 웹 브라우저에 정보를 저장하고 불러오는 수단으로 쿠키가 존재하면, 웹 브라우저는 도메인에게 HTTP 요청 시 쿠키를 함께 전달합니다.

### 3.1. Cookie Option

- Domain: 서버와 요청의 도메인이 일치하는 경우 쿠키 전송
- Path: 서버 요청의 세부 경로가 일치하는 경우 쿠키 전송
- MaxAge or Expires: 쿠키의 유효기간 설정
  - 쿠키는 위 옵션의 여부에 따라 세션 쿠키(Session Cookie)와 영속성 쿠키(Persistent Cookie)로 나눠집니다.
  - **세션 쿠키:** `MaxAge` 또는 `Expires` 옵션이 없는 쿠키로, 브라우저가 실행 중일 때 사용할 수 있는 임시 쿠키입니다. 브라우저를 종료하면 해당 쿠키는 삭제됩니다.
  - **영속성 쿠키:** 브라우저의 종료 여부와 상관없이 `MaxAge` 또는 `Expires`에 지정된 유효시간만큼 사용할 수 있는 쿠키입니다.
- HttpOnly - 스크립트의 쿠키 접근 가능 여부 설정
- Secure - HTTPS에서만 쿠키 전송 여부 설정
- SameSite - 같은 사이트에서만 쿠키를 사용할 수 있게 하는 설정
  - Lax :Cross-Origin 요청이면 'GET' 메소드에 대해서만 쿠키 전송
  - Strict : Cross-Origin이 아닌 `same-site`인 경우에만 쿠키 전송 불가
  - None: 모든 메서드 요청에 대해 쿠키 전송, 다만 쿠키 옵션 중 `Secure` 옵션이 필요

### 3.2. 쿠키를 이용한 상태 유지

이러한 쿠키의 특성을 이용하여 서버는 클라이언트에 인증정보를 담은 쿠키를 전송하고, 클라이언트는 전달받은 쿠키를 요청과 같이 전송하여 Stateless 한 인터넷 연결을 Stateful 하게 유지할 수 있습니다.

**하지만 기본적으로는 쿠키는 오랜 시간 동안 유지될 수 있고, 자바스크립트를 이용해서 쿠키에 접근할 수 있기 때문에 쿠키에 민감한 정보를 담는 것은 위험합니다.**


## 4. Session

서버가 클라이언트에 유일하고 암호화된 ID를 부여하고, 중요 데이터는 서버에서 관리해야 합니다.

### 4.1. 세션 기반 인증 (Session-based Authentication)

#### 로그인

사용자가 만일 정확한 아이디와 비밀번호를 입력했다면, 서버는 인증(Authentication)에 성공했다고 판단할 것입니다.

그렇다면, 다음번에 인증을 필요로 하는 작업(장바구니에 물품 추가)을 요청할 경우,

서버가 **"해당 유저는 인증에 성공했음"을 알고 있다면, 유저가 매번 로그인할 필요가 없을 것입니다.**

> 인증에 따라 리소스의 접근 권한(Authorization) 이 달라집니다.


이때 서버와 클라이언트에 각각 필요한 것이 다음과 같습니다.

- 서버는 사용자가 인증에 성공했음을 알고 있어야 합니다.
- 클라이언트는 인증 성공을 증명할 수단을 갖고 있어야 합니다.

#### 세션과 세션 아이디

- 사용자가 인증에 성공한 상태는 **세션**이라고 부릅니다.
  - 서버는 일종의 저장소에 세션을 저장합니다. 주로 in-memory, 또는 세션 스토어(redis 등과 같은 트랜잭션이 빠른 DB)에 저장합니다.
- 세션이 만들어지면, 각 세션을 구분할 수 있는 **세션 아이디**도 만들어지는데, 보통 클라이언트에 세션 성공을 증명할 수단으로써 세션 아이디를 전달합니다. **이때 웹사이트에서 로그인을 유지하기 위한 수단으로 쿠키를 사용합니다. 쿠키에는 서버에서 발급한 세션 아이디를 저장합니다.**

쿠키를 통해 유효한 세션 아이디가 서버에 전달되고,  세션 스토어에 해당 세션이 존재한다면 서버는 해당 요청에 접근 가능하다고 판단합니다.

하지만 쿠키에 세션 아이디 정보가 없는 경우, 서버는 해당 요청이 인증되지 않았음을 알려줍니다.

### 로그아웃

세션 아이디가 담긴 쿠키는 클라이언트에 저장되어 있으며, 서버는 세션을 저장하고 있습니다. 그리고 서버는 그저 세션 아이디로만 인증 여부를 판단합니다.

> 주의: 쿠키는 세션 아이디, 즉 인증 성공에 대한 증명을 하고 있으므로, 탈취될 경우 서버는 해당 요청이 인증된 사용자의 요청이라고 판단합니다.

그러므로 로그아웃은 다음 두 가지 작업을 해야 합니다.

- 서버 : 세션 정보를 삭제해야 합니다.
- 클라이언트 : 쿠키를 갱신해야 합니다.

서버가 클라이언트의 쿠키를 임의로 삭제할 수는 없습니다. 대신, set-cookie로 클라이언트에게 쿠키를 전송할 때 세션 아이디의 키값을 무효한 값으로 갱신할 수 있습니다.

|            | Cookie                               |Seetion|
|:-----------|:-------------------------------------|:----|
| 설명         | 쿠키는 그저 Http의 stateless를<br> 보완해주는 도구 |접속 상태를 서버가 가짐 (stateful) 접속 상태와 <br>권한 부여를 위해 세션 아이디를 쿠키로 전송|
| 접속상태 저장위치 | 클라이언트                                |서버|
| 장점         | 서버에 부담을 덜어줌                          |신뢰할 수 있는 유저인지 서버에서 확인|
| 단점         | 쿠키 그 자체는 인증이 아님                      |하나의 서버에서만 접속 상태를 가짐 분산에 불리|

### 인증(Authentication)과 권한 부여(Authorization)

1. 인증(Authentication)
   - 사용자(클라이언트)가 본인이 맞는지 확인하는 과정
   - 회원 아이디/패스워드 기반 인증(Spring Security Username/Password 기반 인증)
   - JWT를 통한 자격 검증
   - OAuth2를 이용한 인증(타 서비스에 인증을 위임하는 방식)
   - 2 factor 인증(온라인 뱅킹: 공인 인증서 + 보안 카드 또는 OTP, 주석거래: 로그인 인증 + 공인 인증서)
2. 권한 부여(Authorization)
   - 인증된 사용자(클라이언트)가 어떤 리소스에 대한 적절한 접근 권한을 가졌는지 확인하는 과정
   - 역할 기반의 권한 부여(URL 접근 권한 있는지 확인)
   - 그룹 기반의 권한 부여(Github의 Repository 접근 그룹 지정)


## 5. 웹 보안 공격

### 5.1. SQL Injection

SQL Injection(SQL 삽입)은 웹 해킹을 접한다면 가장 먼저 배우는 공격 기법인 만큼 간단하지만 아주 강력한 공격입니다.

이름처럼 데이터베이스에서 임의의 SQL 문을 실행할 수 있도록 명령어를 삽입하는 공격 유형입니다.

응용 프로그램의 보안상의 허점을 이용해 데이터베이스를 비정상적으로 조작하며, 이에 따라 기록이 삭제되거나 데이터가 유출될 수 있습니다.

#### SQL injection 대응 방안

1. **입력(요청)값 검증**

   SQL 문은 사람이 사용하는 자연어와 비슷하기 때문에 키워드를 막기엔 한계가 있습니다. 따라서 블랙리스트가 아닌 화이트리스트 방식으로 해당 키워드가 들어오면 다른 값으로 치환하여 SQL Injection에 대응할 수 있습니다.

   > 보안에서 화이트리스트란 기본 정책이 모두 차단인 상황에서 예외적으로 접근이 가능한 대상을 지정하는 방식 또는 그 지정된 대상들을 말합니다.

2. **Prepared Statement 구문 사용**

   Prepared Statement 구문을 사용하면 사용자의 입력이 SQL 문으로부터 분리되어 SQL Injection을 방어할 수 있습니다. 사용자의 입력값이 전달되기 전에 데이터베이스가 미리 컴파일하여 SQL을 바로 실행하지 않고 대기하며, 사용자의 입력값을 단순 텍스트로 인식합니다. 따라서 입력값이 SQL 문이 아닌 단순 텍스트로 적용되며 공격에 실패하게 됩니다.

3. **Error Message 노출 금지**

   공격자는 데이터베이스의 Error Message를 통해 테이블이나 칼럼 등 데이터베이스의 정보를 얻을 수 있습니다. 에러가 발생한 SQL 문과 에러 내용이 클라이언트에 노출되지 않도록 별도의 에러핸들링이 필요합니다.


### 5.2. Cross-Site Request Forgery (CSRF)

다른 사이트에서 유저가 보내는 요청(request)을 조작(forgery)하는 것 (eg. 이메일에 첨부된 링크를 누르면 내 은행 계좌의 돈이 빠져나감)

해커가 직접 데이터에 접근할 수 없다. (eg. 다른 사이트이기 때문에 response에 직접 접근할 수 없음)

#### CSRF 공격하기 위한 조건

쿠키를 사용한 로그인 (유저가 로그인했을 때, 쿠키로 어떤 유저인지 알 수 있어야 함)

예측할 수 있는 요청 parameter를 가지고 있어야 함 (request에 해커가 모를 수 있는 정보가 담겨있으면 안 됨)

#### CSRF 공격 막는 방법

CSRF 토큰 사용하기 (서버 측에서 CSRF 공격에 보호하기 위한 문자열을 유저의 브라우저와 웹 앱에만 제공)

Same-site cookie 사용하기 (같은 도메인에서만 세션/쿠키 사용)


#### Refferrer 헤더 정보를 확인

- HTTP 요청헤더(request header)정보에서 Referrer 정보를 확인할 수 있습니다.
- 호스트(host)와 Referrer 값이 보통의 경우 일치하므로 둘을 비교합니다.
- CSRF 공격의 대부분 Referrer 값에 대한 검증만으로도 많은 수의 공격을 방어할 수 있습니다.
- Java servlet을 사용한다면 아래와 같이 intercepter 클래스를 만들어서 모든 요청에 대해 referer check 할 수 있도록 방어 가능합니다.

```java
public class ReferrerCheck implements HandlerInterceptor {
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        String referer = request.getHeader("Referer");
        String host = request.getHeader("host");
        if (referer == null || !referer.contains(host)) {
            response.sendRedirect("/");
            return false;
        }
        return true;
    }
}
```


## Reference

[동일 사이트 및 동일 출처 이해하기](https://web.dev/same-site-same-origin/#same-site-cross-site)

[패스워드의 암호화와 저장](https://st-lab.tistory.com/100)
