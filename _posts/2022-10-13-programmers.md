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
길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 "수박수박"을 리턴하고 3이라면 "수박수"를 리턴하면 됩니다.

### 제한 조건
n은 길이 10,000이하인 자연수입니다.    

**입출력 예**

|n|	return|
|:---:|:----:|
|3|	"수박수"|
|4	|"수박수박"|

*************

## 풀이 코드
처음에 C언어로 풀려고 하다가 내가 생각한 알고리즘으로 코드가 풀리지 않아서 JAVA로 변경하여 해결하였다.
### JAVA
내가 작성한 코드이다.
```java
class Solution {
    public String solution(int n) {
        String answer = "";
        for(int i=1; i<=n; i++){
            if(i%2==1)
                answer = answer + "수";
            else
                answer = answer + "박";
        }
        return answer;
    }
}

```
1부터 n까지 i를 하나씩 증가시키면서 i가 홀수일 경우에는 '수'를 answer에 붙여넣고, 짝수일 경우에는 '박'을 붙여넣는 알고리즘을 작성하였다.

### C언어
#### 처음 작성한 코드(실패)
```c
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
#include <string.h>

char* solution(int n) {
    // 리턴할 값은 메모리를 동적 할당해주세요.
    char* answer = (char*)malloc(sizeof(char)*n);

    for(int i = 1; i <= n; i++) {
        if(i%2 == 1)
            strcat(answer, "수");
        else 
            strcat(answer, "박");
    }

    return answer;
}
```
이렇게 했더니 자꾸 에러가 발생하면서 실행이 되지 않았다.
core dumped에러도 발생하였다.
#### 수정한 코드(성공)
다른 사람의 코드를 참조하여 실수한 부분을 알아낼 수 있었다.
```c
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
#include <string.h>

char* solution(int n) {
    // 리턴할 값은 메모리를 동적 할당해주세요.
    char* answer = (char*)malloc(sizeof(char)*n*3);

    strcpy(answer, "");

    for(int i = 1; i <= n; i++) {
        if(i%2 == 1)
            strcat(answer, "수");
        else 
            strcat(answer, "박");
    }

    return answer;
}
```
한글은 UTF-8이기 때문에 한 글자당 3바이트이므로 동적 할당을 할 때 3을 곱해줘야 한다는 것을 깨달았다.<br>
그리고 answer을 아무글자도 입력되지 않은 상태로 초기화 시켜주는 것이 필요하다는 것을 알 수 있었다.