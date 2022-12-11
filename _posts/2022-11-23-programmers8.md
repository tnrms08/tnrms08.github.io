---
title: x만큼 간격이 있는 n개의 숫자
layout: post
post-image: "https://images.velog.io/images/mickeymouse/post/0cf235fb-bb11-45aa-905c-a9008b8ee5eb/logo.jpg"
description: 프로그래머스 문제의 풀이와 풀며 중요하고 몰랐던 내용들을 정리하였다.
tags:
- programmers
- java
---

# 문제 설명
함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다. 다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

## 제한 조건
x는 -10000000 이상, 10000000 이하인 정수입니다.
n은 1000 이하인 자연수입니다.

## 입출력 예

|x|	n|	answer|
|:---:|:---:|:---:|
|2|	5|	[2,4,6,8,10]|
|4|	3|	[4,8,12]|
|-4|	2|	[-4, -8]|

# 풀이
- 오류난 풀이

```java
class Solution {
    public long[] solution(int x, int n) {
        long[] answer = {};
        //n의 크기를 갖는 배열 정의
        answer = new long[n];
        int num = x;	//배열에 처음 저장하는 숫자를 x로 지정
        for(int i=0;i<n;i++){
            answer[i]=num;
            num += x;	//x만큼 증가시키기
        }
        return answer;
    }
}
```
<br>
처음에 위와 같은 풀이로 작성을 한 후 채점을 하였더니 테스트 13과 14에서 실패가 발생하였다.    
그래서 원인을 살펴보니 answer 배열에 넣을 값을 지정한 num을 int로 지정한 것이 원인이 되었다. int를 long으로 바꾸어 다시 채점하였더니 정답이 되었다.    
answer을 지정할 때 long으로 자료형을 지정해서 그런 것 같다.   


- 정답 풀이

```java
class Solution {
    public long[] solution(int x, int n) {
        long[] answer = {};
        answer = new long[n];
        long num = x;	//num의 자료형을 long으로 지정
        for(int i=0;i<n;i++){
            answer[i]=num;
            num += x;
        }
        return answer;
    }
}

```