---
title: 행렬의 덧셈
layout: post
post-image: "https://velog.velcdn.com/images/codemcd/post/131a0a54-437c-4acf-ba01-c8798c0b7628/Java_Logo.png"
description: 프로그래머스 문제의 풀이와 풀며 중요하고 몰랐던 내용들을 정리하였다.
tags:
- programmers
- java
---

# 문제 설명
행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다. 2개의 행렬 arr1과 arr2를 입력받아, 행렬 덧셈의 결과를 반환하는 함수, solution을 완성해주세요.

## 제한 조건
행렬 arr1, arr2의 행과 열의 길이는 500을 넘지 않습니다.

## 입출력 예
|arr1	|arr2|	return|
|:---:|:---:|:---:|
|[[1,2],[2,3]]	|[[3,4],[5,6]]	|[[4,6],[7,9]]|
|[[1],[2]]	|[[3],[4]]	|[[4],[6]]|

# 풀이
```java
class Solution {
    public int[][] solution(int[][] arr1, int[][] arr2) {
        int[][] answer = {};
        //입력받은 행렬의 크기와 동일한 크기의 answer 정의
        answer = new int[arr1.length][arr1[0].length];
        
        //배열의 덧셈
        for(int i = 0 ;i<arr1.length;i++){
            for(int j=0;j<arr1[0].length;j++){
            	//arr1의 값과 arr2의 값을 더한 후 answer에 지정
                answer[i][j]=arr1[i][j]+arr2[i][j];
            }
        }
        
        return answer;
    }
}
```
나는 행렬의 크기만 고려하여 새로운 행렬을 선언하였는데 다른 사람들의 풀이를 보니 처음에 행렬을 입력받은 행렬 중 하나인 arr1이나 arr2로 지정하는 좀 더 간단한 방법이 있다는 것을 알게되었다.

### 다른 사람의 코드
아래는 다른 사람의 코드를 참고하며 주석을 추가한 것이다.

```java
class Solution {
    public int[][] solution(int[][] arr1, int[][] arr2) {
        int[][] answer = {};
        
        //answer의 값들을 arr1의 값과 동일하게 지정
        //=> answer의 크기를 따로 지정하지 않아도 자동적으로 정해진다.
        answer = arr1;
        
        for(int i=0; i<arr1.length; i++){
            for(int j=0; j<arr1[0].length; j++){
            	//기존 answer의 값에 arr2의 값을 더한다.
                answer[i][j] += arr2[i][j];
            }
        }
        return answer;
    }
}

```
