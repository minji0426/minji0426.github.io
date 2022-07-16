---
title: '[blog] 게시글 안올라가는 오류해결(deploy error)'
author: minji0426
date: 2022-07-16 14:31:00 +0900
categories: [blog]
tags: [blog]
---

## ❗️ 오류상황

며칠전 게시글을 작성에서 올리는데

![0](https://user-images.githubusercontent.com/35446812/179341558-3c3a0903-01f7-480b-9e20-f2da09ffb92f.PNG)

빨간불이 들어왔다...

그리고 문제는 이 이후에 푸쉬하는게 다 오류가 발생했다.

<img src="https://user-images.githubusercontent.com/35446812/179342957-96ccb845-2536-4210-8a65-605b8a20f48d.PNG" width="400" />



## 🔍 원인

결론부터 말하자면, 간단한 마크다운 문법 오류였다😅

<img src="https://user-images.githubusercontent.com/35446812/179341561-441669ee-b62a-4856-97ce-5dc5e151daed.PNG" width="350" />

![2](https://user-images.githubusercontent.com/35446812/179341565-804c5ec1-97a1-48df-9205-0f5096df1866.PNG)

```
Error: Process completed with exit code 1.
```

처음엔 빨간 부분만 보고 구글에 검색해봤는데 해결방법을 찾지 못했다.

그런데 자세히 보니까 중간에 저 주저리주저리 써있는 게시글의 내용이 그냥 내 게시글 md파일의 전체 내용을 보여주는건 줄 알고 쓱 보고 넘겼었는데 특정 부분 이후 내용부터 적혀있다는것을 깨달았다...!

해당 파일의 저 부분을 전부 주석처리하고 다시 푸쉬해보니

<img src="https://user-images.githubusercontent.com/35446812/179343660-60f1e6ec-e968-4d87-8e48-7569efb6fe2f.PNG" width="500" />

성공!🥳

그리고 자세히 보니 위에 이런 메시지도 있었다.


```
* 11:2102: ERROR: Invalid first code point of tag name U+C774.
```

이 오류 메시지를 검색하다가 \< \>  👈 이 부분이 문제였다는 사실을 알게 되었다.  

내가 이걸 `하이라이트`하겠다고 \`\< \>\` 이렇게 썼었고, 

\` \` 👈이거 안에 백슬래쉬를 사용하면 \\< \\> 이렇게 보여지길래 생략해도 되는 줄 알았다.


## 💡 해결 방법

\` \` 이걸 지우고, \< \> 👉 \\< \\> 이렇게 바꿔서 해결하였다.



## References
- [git action 자동 배포 에러 해결기 (ERROR: Invalid first code point of tag name U+C804.)](https://seobie.github.io/blog/git-action-struggles)