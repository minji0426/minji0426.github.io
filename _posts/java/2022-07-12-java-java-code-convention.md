---
title: '[Java] 자바 코드 컨벤션 (Java code convention)'
author: minji0426
date: 2022-07-12 16:34:30 +0900
categories: [TIL, Java]
tags: [TIL, Java, convention]
---

## Introduction

### 컨벤션(convention)이란?

convention은 협약, 관례라는 뜻이다.

코드 컨벤션이란 읽고, 관리하기 쉬운 코드를 작성하기 위한 코딩 스타일 규약, 작성 표준을 의미한다.

이 [문서](https://naver.github.io/hackday-conventions-java/)를 읽고 내용을 정리해보려고 한다.


## 📚 Java code convention

### ✔️이름
- 식별자에는 영문/숫자/언더스코어만 허용

- 한국어 발음대로 표기 금지 

- 패키지
    - 소문자로 구성
    - 대문자, 언더스코어( _ ) 금지

- 클래스
    - 대문자 카멜표기법
    - 명사 사용
    - 테스트 클래스는 'Test’로 끝남

- 인터페이스
    - 대문자 카멜표기법
    - 명사/형용사 사용

- 메서드 
    - 소문자 카멜표기법 - 첫 번째 단어를 소문자로 작성하고, 이어지는 단어의 첫 글자를 대문자로 작성
    - 동사/전치사로 시작
    - 테스트 클래스의 메서드 이름에서는 언더스코어를 허용

- 상수
    - 대문자
    - 복합어일 때 언더스코어 사용

- 변수
    - 소문자 카멜표기법
    - 임시 변수 외에는 1 글자 이름 사용 금지


### ✔️선언
- 탑레벨 클래스(Top level class)는 소스 파일에 1개만 존재
- static import에만 와일드 카드 허용
- 제한자 선언의 순서
- annotation 선언 후 새줄 사용
- 한 줄에 한 문장
- 하나의 선언문에는 하나의 변수만
- 배열에서 대괄호는 타입 뒤에 선언
- `long`형 값의 마지막에 `L`붙이기
- 특수 문자의 전용 선언 방식을 활용


### ✔️들여쓰기
- 하드탭 사용
    - 스페이스를 사용하지 않는다.
- 탭의 크기는 4개의 스페이스
- 블럭 들여쓰기
    - 클래스, 메서드, 제어문 등의 코드 블럭이 생길 때마다 1단계를 더 들여쓴다.


### ✔️중괄호 { }

#### 클래스, 매서드, 제어문의 블럭을 구분

- K&R 스타일로 중괄호 선언
    ```java
    public class SearchConditionParser {
    public boolean isValidExpression(String exp) {

        if (exp == null) {
            return false;
        }

        for (char ch : exp.toCharArray()) {
            ....
        }

        return true;
        }
    }
    ```

- 닫는 중괄호와 같은 줄에 else, catch, finally, while 선언
- 빈 블럭에 새줄 없이 중괄호 닫기 허용
    - ex) public void close() {}
- 조건/반복문에 중괄호 필수 사용



### ✔️줄바꿈

#### 작성한 명령어가 줄 너비를 초과했을 경우 코드 가독성을 위해서 강제로 줄을 바꾸는 것

- 최대 줄 사용 너비는 120자
- package,import 선언문은 한 줄로
    - 최대 줄수를 초과하더라도 한 줄로 쓴다.
- 줄바꿈 후 추가 들여쓰기
    ```java
    AbstractAggregateRootTest.AggregateRoot proxyAggregateRoot =
        em.getReference(AbstractAggregateRootTest.AggregateRoot.class, aggregateRoot.getId());
    ```
- 줄바꿈 허용 위치
    - extends 선언 후

    - implements 선언 후

    - throws 선언 후

    - 시작 소괄호(() 선언 후

    - 콤마(,) 후

    - . 전

    - 연산자 전


### ✔️빈줄

#### 명령문 그룹의 영역을 표시하기 위하여 사용

- package 선언 후 빈 줄 삽입
- import 선언의 순서와 빈 줄 삽입
    - 순서
        1. static imports
        2. java.
        3. javax.
        4. org.
        5. net.
        6. 8~10을 제외한 com.*
        7. 1~6, 8~10을 제외한 패키지에 있는 클래스
        8. com.nhncorp.
        9. com.navercorp.
        10. com.naver.
    - 각 그룹 사이에는 빈줄을 삽입
    - 같은 그룹 내에서는 알파벳 순으로 정렬

- 메소드 사이에 빈 줄 삽입


### ✔️공백

- 공백으로 줄을 끝내지 않음
- 대괄호[ ] 뒤에 공백 삽입
- 중괄호의 시작 전, 종료 후에 공백 삽입
    ```java
    public void printWarnMessage(String line) {
        if (line.startsWith(WARN_PREFIX)) {
            ...
        } else {
            ...
        }
    }
    ```
- 제어문 키워드와 여는 소괄호 사이에 공백 삽입
    ```java
    if (maxLine > LIMITED) {
        return false;
    }
    ```
- 식별자와 여는 소괄호 사이에 공백 X
- 타입 캐스팅에 쓰이는 소괄호 내부 공백 X
- 제네릭스 산괄호의 공백 규칙
    ```java
    public static <A extends Annotation> A find(AnnotatedElement elem, Class<A> type) { // 제네릭스 메서드 선언
        List<Integer> l1 = new ArrayList<>(); // '(' 가 바로 이어질때
        List<String> l2 = ImmutableList.Builder<String>::new; // 메서드 레퍼런스가 바로 이어질 때
        int diff = Util.<Integer, String>compare(l1, l2); // 메서드 이름이 바로 이어질 때
    }
    ```
- 콤마( , )/구분자 세미콜론( ; )의 뒤에만 공백 삽입
- 콜론( : )의 앞 뒤에 공백 삽입
- 이항/삼항 연산자의 앞 뒤에 공백 삽입
- 단항 연산자와 연산 대상 사이에 공백 X
- 주석문 기호 전후의 공백 삽입

    ```java
    /*
    * 공백 후 주석내용 시작
    */

    System.out.print(true); // 주석 기호 앞 뒤로 공백

    /* 주석내용 앞에 공백, 뒤에도 공백 */
    ```



## References
- [캠퍼스 핵데이 Java 코딩 컨벤션](https://naver.github.io/hackday-conventions-java/)