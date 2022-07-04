---
title: '[SpringBoot] Spring Boot, IntelliJ - invalid source release 오류 해결'
author: minji0426
date: 2022-07-04 23:03:30 +9000
categories: [TIL, SpringBoot]
tags: [TIL, SpringBoot]
---

## 오류 메세지
    Execution failed for task ':compileJava'. > invalid source release: 11
- gradle에 설정된 JDK 버전과 IntelliJ에 설정된 JDK 버전이 다르기 때문이다.
 </br>

 - 우선 오류 메세지 끝에 숫자(11)에 맞는 버전이 설치되어 있는지 확인하고 맞는 버전의 JDK를 설치하자 [JDK 11 설치하기](https://www.oracle.com/kr/java/technologies/javase/jdk11-archive-downloads.html)
</br>
 ex) 17이면 17버전을 설치하면 된다.

</br>
</br>

## 해결 방법
    - 프로젝트 JDK 설정
    - gradle JDK 설정

- File -> Project Structure</br></br>
![png1](https://i.esdrop.com/d/f/7EjyucZQG9/YZvJF9FnyP.png)
(+)버튼 눌러서 JDK 추가하기 </br></br>
![png2](https://i.esdrop.com/d/f/7EjyucZQG9/vEEghQjLuf.png)
![png3](https://i.esdrop.com/d/f/7EjyucZQG9/I3hPUKYe8H.png)

</br>

- File -> Settings</br></br>
![png4](https://i.esdrop.com/d/f/7EjyucZQG9/PX13M2TgEc.png)
![png5](https://i.esdrop.com/d/f/7EjyucZQG9/8Bo75fN4Hs.png)

</br>

## References
- [Execution failed for task ':compileJava'. > invalid source release: 11](https://velog.io/@kcho32/Execution-failed-for-task-compileJava.-invalid-source-release-11)