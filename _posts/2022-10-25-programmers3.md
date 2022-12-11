---
title: 수박수박수박수박수박수?
layout: post
post-image: "https://velog.velcdn.com/images/codemcd/post/131a0a54-437c-4acf-ba01-c8798c0b7628/Java_Logo.png"
description: 프로그래머스 문제의 풀이와 풀며 중요하고 몰랐던 내용들을 정리하였다.
tags:
- programmers
- java
---

## 문제 설명
대문자와 소문자가 섞여있는 문자열 s가 주어집니다. s에 'p'의 개수와 'y'의 개수를 비교해 같으면 True, 다르면 False를 return 하는 solution를 완성하세요. 'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴합니다. 단, 개수를 비교할 때 대문자와 소문자는 구별하지 않습니다.

예를 들어 s가 "pPoooyY"면 true를 return하고 "Pyy"라면 false를 return합니다.

### 제한사항
문자열 s의 길이 : 50 이하의 자연수
문자열 s는 알파벳으로만 이루어져 있습니다.
### 입출력 예
|s|	answer|
|:---:|:----:|
|"pPoooyY"|	true|
|"Pyy"|	false|
### 입출력 예 설명
- 입출력 예 #1
'p'의 개수 2개, 'y'의 개수 2개로 같으므로 true를 return 합니다.
- 입출력 예 #2
'p'의 개수 1개, 'y'의 개수 2개로 다르므로 false를 return 합니다.
-----------------
## 풀이 코드
```java
class Solution {
    boolean solution(String s) {
        char[] charArr = s.toCharArray();
        boolean answer = true;
        
        int nP = 0; //p의 개수
        int nY 0; //y의 개수
        
        for(int i=0; i<s.length();i++){
            if(charArr[i]=='p'||charArr[i]=='P')
                nP;
            else if(charArr[i]=='y'||charArr[i]=='Y')
                nY;
        }
        
        if(nP==nY) answer = true;
        else answer = false;

        return answer;
    }
}
```
### 다른 사람의 풀이

다른 사람들의 풀이를 살펴보니 나처럼 소문자일 경우와 대문자일 경우를 나눠서 if문을 사용하지 않고, 주어진 문장을 모두 소문자나 대문자로 변경하여 if문을 사용하였다.
> #### toLowerCase();
- 모두 소문자로 변경
```java
s=s.toLowerCase();
```
#### toUpperCase();
- 모두 대문자로 변경
```java
s=s.toUpperCase();
```

------------------
## 관련 내용
### toCharArray();
JAVA에서는 문자열에서의 인덱스 접근이 불가능하다.
그렇기 때문에 toCharArray() 함수를 이용하여 문자열을 char형의 배열로 변경시켜준 후 인덱스 접근을 사용해야 한다.
```java
char[] charArr = s.toCharArray();
```
### charAt();
문자열에서 해당 인덱스의 값을 가져오기 위해 사용한다.
괄호 안에는 인덱스 숫자를 넣어 해당 인덱스의 문자를 가져오도록 한다.
```java
String s = "test string";
char test = s.charAt(6);	//test = 't'; (char)
```
#### String.valueOf();
위에서 CharAt()을 이용하여 char 형태로 받아온 값을 다시 String 형태로 변경하는 것이다.
```java
String.valueOf(test);	//'t' (String)
```