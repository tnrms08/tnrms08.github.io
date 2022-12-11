---
title: 제일 작은 수 제거하기
layout: post
post-image: "https://images.velog.io/images/mickeymouse/post/0cf235fb-bb11-45aa-905c-a9008b8ee5eb/logo.jpg"
description: 프로그래머스 문제의 풀이와 풀며 중요하고 몰랐던 내용들을 정리하였다.
tags:
- programmers
- java
---

# 문제 설명
정수를 저장한 배열, arr 에서 가장 작은 수를 제거한 배열을 리턴하는 함수, solution을 완성해주세요. 단, 리턴하려는 배열이 빈 배열인 경우엔 배열에 -1을 채워 리턴하세요. 예를들어 arr이 [4,3,2,1]인 경우는 [4,3,2]를 리턴 하고, [10]면 [-1]을 리턴 합니다.

## 제한 조건
arr은 길이 1 이상인 배열입니다.
인덱스 i, j에 대해 i ≠ j이면 arr[i] ≠ arr[j] 입니다.

## 입출력 예

|arr|	return|
|:---:|:---:|
|[4,3,2,1]	|[4,3,2]|
|[10]	|[-1]|

----------------

# 코드
```java
import java.util.ArrayList;
import java.util.Arrays;

class Solution {
    public int[] solution(int[] arr) {
        int[] answer = {};
        int min = arr[0];

		//동적배열 선언
        ArrayList<Integer> list = new ArrayList<Integer>();
        
        //배열 arr에서 가장 작은 수 찾아 min에 저장
        for(int i = 0 ; i<arr.length;i++){
            if(arr[i]<min)
                min = arr[i];
        }
        
        //min값을 제외하고 list에 저장
        for(int i = 0 ; i<arr.length;i++){
            if(arr[i]!=min){
                list.add(arr[i]);
            }
        }
        
        //list의 크기가 0일 경우 -1 반환
        if(list.size()==0){
            answer = new int[1];	//answer의 크기 지정
            answer[0]=-1;
        }
        //list의 크기가 0이 아닐 경우 list의 값 answer로 이동
        else{
            answer = new int[list.size()];
            for(int i=0;i<list.size();i++){
                answer[i] = list.get(i);
            }
        }
        return answer;
    }
}
```

이전에 작성했던 글에서 List 관련 부분을 보고 참고하여 문제를 풀었다.     
[[JAVA]두 개 뽑아서 더하기](https://velog.io/@2020108249/JAVA%EB%91%90-%EA%B0%9C-%EB%BD%91%EC%95%84%EC%84%9C-%EB%8D%94%ED%95%98%EA%B8%B0)

## 정리
이번 문제를 풀면서 List의 개념을 다시 파악했고, answer의 크기를 지정해주는 것이 필수라는 것을 알았다.      
JAVA에서 배열을 이용하려면 Array와 List의 개념과 기능들을 확실히 아는 것이 필요한 것 같다.