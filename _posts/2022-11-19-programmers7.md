---
title: 소수 찾기
layout: post
post-image: "https://velog.velcdn.com/images/codemcd/post/131a0a54-437c-4acf-ba01-c8798c0b7628/Java_Logo.png"
description: 프로그래머스 문제의 풀이와 풀며 중요하고 몰랐던 내용들을 정리하였다.
tags:
- programmers
- java
---

# 문제 설명
1부터 입력받은 숫자 n 사이에 있는 소수의 개수를 반환하는 함수, solution을 만들어 보세요.    

소수는 1과 자기 자신으로만 나누어지는 수를 의미합니다.    
(1은 소수가 아닙니다.)     

## 제한 조건
n은 2이상 1000000이하의 자연수입니다.

## 입출력 예

|n|	result|
|:---:|:---:|
|10|	4|
|5	|3|

### 입출력 예 설명

#### 입출력 예 #1
1부터 10 사이의 소수는 [2,3,5,7] 4개가 존재하므로 4를 반환

#### 입출력 예 #2
1부터 5 사이의 소수는 [2,3,5] 3개가 존재하므로 3를 반환

-------------------------------------------------
# 코드

## 1

```java
class Solution {
    public int solution(int n) {
        int answer = 0;
        for(int i=2;i<=n;i++){
            boolean flag = true;
            //소수인지 판별
            for(int j=2;j<=Math.sqrt(i);j++){
                if(i%j==0){
                    flag = false;
                    break;
                }
            }
            if(flag == true)
                answer++;
        }
        
        return answer;```

    }
}
```
## 2. 함수 생성

```java
class Solution {
	//소수인지 판별하는 함수
    public boolean sosu(int n){
        boolean answer = true;
        for(int i=2;i<=Math.sqrt(n);i++){
            if(n%i==0){
                answer = false;
                break;
            }
        }
        return answer;
    }
    
    public int solution(int n) {
        int answer = 0;
        for(int i=2;i<=n;i++){
        	//i값이 소수라면
            if(sosu(i) == true)
                answer++;
        }
        return answer;
    }
}
```

-----------------
# 관련 내용

## 소수 판별법
1. 2부터 n-1까지 나눠보기
2. 2부터 n/2까지 나눠보기    
>  자기자신을 제외하고 절반을 초과하는 숫자에서 나눴을때 나머지가 0이되는 숫자는 나올수가 없다.
3. 2부터 √n 까지 나눠보기    
> 약수들의 곱으로 봤을때 루트를 씌운 값이 중간값이 되므로 √n 까지 확인해도 된다.

**3번 판별법이 가장 효율적이다.**
