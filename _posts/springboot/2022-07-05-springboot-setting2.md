---
title: '[SpringBoot] Spring Boot - CMD에서 build 오류 해결(invalid source release)'
author: minji0426
date: 2022-07-05 11:46:30 +0900
categories: [TIL, SpringBoot]
tags: [TIL, SpringBoot, CMD, JDK]
---
## 윈도우에서 스프링부트 빌드 하는 법
- cmd 
    1. 프로젝트 디렉토리로 이동
    2. gradlew \<enter\> 
    3. gradlew build \<enter\> 

## ❗️ 오류 메세지

> Execution failed for task ':compileJava'. > invalid source release: 11  
 
  
## 🔍 원인
 위의 오류 메세지는 [이전 포스팅](https://minji0426.github.io/posts/springboot-setting/)과 똑같다.  

 IntelliJ에서 빌드 할 때는 프로젝트 구성에서 바꿔준 JDK를 이용하여 빌드가 되지만, gradlew.bat는 프로젝트가 사용하는 JDK의 경로를 알지 못하기 때문에 위와 같은 오류가 한 번 더 발생했다.



## 💡 해결 방법

### - 환경변수 편집


> 내 PC 우 클릭> 속성 > 고급 시스템 설정 > 환경 변수

1. 시스템 변수 > 새로 만들기  
-변수 이름: JAVA_HOME  
-변수 값: JDK의 경로 입력  
\> 확인

2. 시스템 변수 중 Path 편집  
-새로 만들기 > %JAVA_HOME%\bin 입력 > 확인  

---
나는 여기까지해도 해결이 되지않아 사용자 변수도 편집해주었다.  

1. 사용자 변수 > 새로 만들기  
-변수 이름: JAVA_HOME  
-변수 값: JDK의 경로 입력  
\> 확인
2. 사용자 변수 중 Path 편집
JDK의 경로 입력 \> 확인






## References
- [인프런 질의응답](https://www.inflearn.com/questions/471804)
- [[IntelliJ] Cause: invalid source release: 11 에러](https://charliecharlie.tistory.com/315)