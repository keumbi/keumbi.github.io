---
title: gradlew Permission 실패
author: keumbi
date: 2022-11-15 11:20:00 +0900
categories: [Error Handling Log]
tags: [spring build, error, bug fix]
---

## 이슈
빌드하고 실행하기 도중 에러 발생!!

콘솔로 이동
```
./gradlew build // (1)
cd build/libs
java -jar hello-spring-0.0.1-SNAPSHOT.jar
// 실행 확인
```
위에 내용을 실행 중 (1)을 터미널에 입력했을 때 permission denied: ./gradlew 에러가 발생 됐다.

## 에러 메시지
![에러](/assets/img/img-gradlew-error.png){:.shadow style="max-width: 60%" }
```
permission denied: ./gradlew
```

## 해결 방법
![img.png](/assets/img/img-gradlew-error2.png){:.shadow style="max-width: 60%" }

`chmod +x gradlew` 입력

```
chmod +x gradlew

./gradlew build

```

아래 참고 링크에 가면 다양한 해결 방법이 있다. 원하는 방법으로 잘 해결하시길...🥹

## Reference

[gradlew: Permission Denied](https://stackoverflow.com/questions/17668265/gradlew-permission-denied)


