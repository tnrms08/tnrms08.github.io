---
title: [프로그래머스, JAVA]서울에서 김서방 찾기
layout: post
post-image: "https://velog.velcdn.com/images/codemcd/post/131a0a54-437c-4acf-ba01-c8798c0b7628/Java_Logo.png"
description: 프로그래머스 문제의 풀이와 풀며 중요하고 몰랐던 내용들을 정리하였다.
tags:
- programmers
- java
---


# 문제 설명
String형 배열 seoul의 element중 "Kim"의 위치 x를 찾아, "김서방은 x에 있다"는 String을 반환하는 함수, solution을 완성하세요. seoul에 "Kim"은 오직 한 번만 나타나며 잘못된 값이 입력되는 경우는 없습니다.

## 제한 사항
seoul은 길이 1 이상, 1000 이하인 배열입니다.
seoul의 원소는 길이 1 이상, 20 이하인 문자열입니다.
"Kim"은 반드시 seoul 안에 포함되어 있습니다.
### 입출력 예
|seoul|	return|
|:---:|:---:|
|["Jane", "Kim"]|	"김서방은 1에 있다"|
# 풀이 코드
```java
class Solution {
    public String solution(String[] seoul) {
        String answer = "";
        for(int i=0;i<seoul.length;i++){
            if(seoul[i].equals("Kim"))
                answer = "김서방은 "+i+"에 있다";
        }
        return answer;
    }
}

```
이번 문제의 풀이는 간단하기 때문에 인터넷 검색을 통해 찾은 개념 하나만 설명하고 지나가도록 하겠습니다.
#### equals()
정수인 경우에는 '=='를 통해 숫자가 같은지 다른지 비교를 수행하지만 문자열의 경우에는 숫자와 동일한 방법으로 같은지 비교할 수 없기 때문에 equals라는 함수를 사용합니다.
> #### a.equals(b)
- 문자열 a와 b가 동일한 경우에는 true를 반환합니다.

#### 참고
문자열 비교에서의 '=='는 각 문자열의 주소값을 비교하는 것이라고 합니다.