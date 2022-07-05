---
title: '[SpringBoot] Spring Boot - Port 8080 is already in use'
author: minji0426
date: 2022-07-05 12:53:30 +0900
categories: [TIL, SpringBoot]
tags: [TIL, SpringBoot, CMD]
---

## ❗️ 오류 메세지

> Port 8080 is already in use  
 
  
## 🔍 원인
 포트번호가 이미 사용중인 상태이다.


## 💡 해결 방법
> 1. 포트를 변경한다.
> 2. 포트를 사용하고 있는 프로세스를 종료시킨다. 

### 8080 포트를 사용 중인 프로세스 종료시키기  
- cmd 관리자 권한으로 실행

```
netstat -ano | findstr 8080

taskkill /F /pid (pid번호)

```

ex)
![png](https://i.esdrop.com/d/f/7EjyucZQG9/InMjF8JSqW.png)



## References
- [[SpringBoot] 에러 spring boot port already in use](https://ninearies.tistory.com/186)