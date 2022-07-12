---
title: '[Git] Git 커밋 메시지 컨벤션 (Git commit message convention - AngularJS)'
author: minji0426
date: 2022-07-12 23:49:10 +0900
categories: [TIL, Git]
tags: [TIL, Git, commit, convention]
---

## Instruction

지금까지 나는 깃에 커밋을 할 때 커밋메시지를 신경써본 적이 없다.

깃이 협업에 필요하다는 것을 알았지만 그냥 사용법만 알면 되는줄 알았다.

하지만 커밋 메시지를 `가독성` 있게 작성을 해야 팀원이 내가 무엇을 커밋한 것인지 알기 쉬워지며, 내가 어떤 코드를 어디에서 작성했는지 쉽게 찾을 수 있어서 `유지보수`가 쉬워진다.

커밋 메시지는 딱히 정해진 형식이 존재하는 것은 아니고, 팀마다 원칙을 정하면 된다.

일반적으로 `Udacity`나 `AngularJS` 스타일을 따른다.

이번 포스팅에서는 AngularJS에 대해 다뤄보고 Udacity는 다음에 다뤄보도록 하겠다.


## 📚 Git commit message convention

### ✔️좋은 git 커밋 메시지를 작성하기 위한 7가지 방법

1. 제목과 본문을 한 줄 띄워 분리하기
2. 제목은 영문 기준 50자 이내로(가독성)
(영어 2글자 = 한글 1글자이기 때문에, 한글 기준으로는 약 30자정도로 작성하면 된다.)
3. 제목 첫글자를 대문자로 (영어만 해당)
4. 제목 끝에 . 금지
5. 제목은 명령조 → 과거형x, 현재형o (ex. 수정했음x, 수정함x, 수정o)
6. 본문은 영문 기준 72자마다 줄 바꾸기
7. 본문은 어떻게보다 `무엇을`, `왜`에 맞춰 작성하기

### ✔️AngularJS

#### 📝커밋 메시지의 형식

```
<type>(<scope>): <short summary>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

#### 📌헤더
`<type>(<scope>): <short summary>`

- \<type>에 들어갈 수 있는 항목들
    - `feat` : 새로운 기능 추가
    - `fix` : 버그 수정
    - `docs` : 문서 관련
    - `style` : 스타일 변경 (포매팅 수정, 들여쓰기 추가, …)
    - `refactor` : 코드 리팩토링
    - `test` : 테스트 관련 코드
    - `build` : 빌드 관련 파일 수정
    - `ci` : CI 설정 파일 수정
    - `perf` : 성능 개선
    - `chore` : 그 외 자잘한 수정

- \<scope>에 들어갈 수 있는 항목들

    - 어디가 변경되었는지, 변경된 부분은 모두 들어갈 수 있다.
    <br>
    예를 들어, $location, $browser, $compile, $rootScope, ngHref, ngClick, ngView
    - scope는 생략 가능하다.

- \<short summary> 요약 설명
    - 명령문, `현재 시제`로 작성
    - 첫글자 대분자X `소문자`로 작성
    - 마지막에 `마침표(.) 금지`

#### 📌Message Body

- 명령문, 현재 시제 권장
- 변경한 이유와 변경 전과의 차이점 설명

#### 📌Message Footer
- 주요 변경 내역들
    - 변경 설명 (description of the change)
    - 변경 사유 (justification)
    - 마이그레이션 지시 (migration instructions)

- 해결된 이슈

    - 해결된 이슈는 커밋 메시지 하단에 Closes #<이슈번호> 와 같이 기록되어야 한다.

    - 예시
        ```
        Closes #234

        Closes #123, #245, #992
        ```

#### 📌예시
```
feat($browser): onUrlChange event (popstate/hashchange/polling)

Added new event to $browser:
- forward popstate event if available
- forward hashchange event if popstate not available
- do polling when neither popstate nor hashchange available

Breaks $browser.onHashChange, which was removed (use onUrlChange instead)
```
```
fix($compile): couple of unit tests for IE9

Older IEs serialize html uppercased, but IE9 does not...
Would be better to expect case insensitive, unfortunately jasmine does
not allow to user regexps for throw expectations.

Closes #392
Breaks foo.bar api, foo.baz should be used instead
```
```
docs(guide): updated fixed docs from Google Docs

Couple of typos fixed:
- indentation
- batchLogbatchLog -> batchLog
- start periodic checking
- missing brace
```


## References
- [AngularJS Commit Message Conventions](https://gist.github.com/stephenparish/9941e89d80e2bc58a153)

- [좋은 git 커밋 메시지를 작성하기 위한 7가지 약속](https://velog.io/@rladpwl0512/Git-commit-%EB%A9%94%EC%8B%9C%EC%A7%80-%EC%BB%A8%EB%B2%A4%EC%85%98)
