---
title: 정수 내림차순으로 배치하기
layout: post
post-image: "https://programmers.co.kr/assets/img-meta-programmers-e00862a7c9acd8ef5164f8c85b3ab0127d083ab59b3a98d7219690bd3570bf35.png"
description: 프로그래머스 문제의 풀이와 풀며 중요하고 몰랐던 내용들을 정리하였다.
tags:
- programmers
- java
---



# 문제 설명
함수 solution은 정수 n을 매개변수로 입력받습니다. n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 예를들어 n이 118372면 873211을 리턴하면 됩니다.

## 제한 조건
n은 1이상 8000000000 이하인 자연수입니다.

## 입출력 예

|n|	return|
|:---:|:---:|
|118372	|873211|

# 풀이

## 코드

```java
import java.util.*;

class Solution {
    public long solution(long n) {
        long answer = 0;
        
        //숫자를 문자열로 변경
        String str = Long.toString(n);
        
        //동적배열(list) 선언
        ArrayList<Character> list = new ArrayList<Character>();
        //list에 문자열의 값들을 하나씩 삽입
        for(int i=0;i<str.length();i++){
            list.add(str.charAt(i));
        }
        
        //내림차순 정렬
        list.sort(Comparator.reverseOrder());
        
        //list를 다시 문자열로 변환
        String tmp = "";
        for(int i=0;i<list.size();i++){
        	//list의 값들을 하니씩 가져와서 문자열에 더하기
            tmp += list.get(i);
        }
        
        //문자열을 정수로 변환
        answer = Long.parseLong(tmp);
        return answer;
    }
}
```

## 개념

### 정수 -> 문자열

```java
int n = 123456;

//1. String.ValueOf()
String str = Sring.ValueOf(n);

//2. Integer.toString()
String str = Integer.toString(n);	//정수->문자열
String str = Long.toStrign(n);		//Long -> 문자열
String str = Array.toString(n);		//배열 -> 문자열

//3. ""+숫자
String str = "" + n;
```
### 문자열 -> 배열

1. 반복문 사용
```java
String str = "123456"l=;

//str의 길이만큼 배열 생성
char[] arr = new char[str.length()];

//한글자씩 배열에 삽입
for (int i = 0; i < str.length(); i++) {
 	arr[i] = str.charAt(i); 
 }
```
<br>

2. toCharArray 메소드 사용
```java
String str = "123456";

//문자열 -> 배열로 변환    
char[] arr = str.toCharArray();
```

### 동적배열 정렬
https://hianna.tistory.com/569    
여기가 정리가 잘 되어 있어서 참고하면 될 것 같다.
### 문자열 -> 정수

```java
String str = "123456";

//문자열 -> 정수
int intValue = Integer.parseInt(str);

//문자열 -> Long
long longValue = Long.parseLong(str);
```
