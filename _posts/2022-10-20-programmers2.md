---
title: 두 개 뽑아서 더하기
layout: post
post-image: "https://images.velog.io/images/mickeymouse/post/0cf235fb-bb11-45aa-905c-a9008b8ee5eb/logo.jpg"
description: 프로그래머스 문제의 풀이와 풀며 중요하고 몰랐던 내용들을 정리하였다.
tags:
- programmers
- java
---

# 문제 설명
정수 배열 numbers가 주어집니다. numbers에서 서로 다른 인덱스에 있는 두 개의 수를 뽑아 더해서 만들 수 있는 모든 수를 배열에 오름차순으로 담아 return 하도록 solution 함수를 완성해주세요.

## 제한 사항
- numbers의 길이는 2 이상 100 이하입니다.
- numbers의 모든 수는 0 이상 100 이하입니다.

<br>
## 입출력 예

|numbers	|result|
|:----:|:----:|
|[2,1,3,4,1]|	[2,3,4,5,6,7]|
|[5,0,2,7]	|[2,5,7,9,12]|

### 입출력 예 설명
#### 입출력 예 #1

- 2 = 1 + 1 입니다. (1이 numbers에 두 개 있습니다.)
- 3 = 2 + 1 입니다.
- 4 = 1 + 3 입니다.
- 5 = 1 + 4 = 2 + 3 입니다.
- 6 = 2 + 4 입니다.
- 7 = 3 + 4 입니다.
- 따라서 [2,3,4,5,6,7] 을 return 해야 합니다.


# 코드

```java
import java.util.ArrayList;
import java.util.Arrays;

class Solution {
    public int[] solution(int[] numbers) {
        int[] answer = {};
        
        ArrayList<Integer> list = new ArrayList<Integer>();

        for(int i=0;i<numbers.length-1;i++){
            for(int j=i+1;j<numbers.length;j++){
                int temp = numbers[i]+numbers[j];
                if (list.indexOf(temp) < 0){
                	list.add(temp);
                }
            }
        }
        
        answer = new int[list.size()];
        for (int i = 0; i < list.size(); i++) {
            answer[i] = list.get(i);
        }
        Arrays.sort(answer);

        return answer;
    }
}
```


아래에 작성한 ArrayList관련 함수를 보고나면 위에 코드가 이해될 것이다.    
<br>

# 관련 정보

### ArrayList
동적배열을 구현하기 위해 사용한다.   
<br>

#### 관련 함수
```java
//ArrayList 선언(정수형)
ArrayList<Integer> list = new ArrayList<Integer>();

//list의 마지막에 데이터 추가
list.add(temp);

//index 1에 temp 추가하기
list.add(1,temp);

//index 1의 값을 5로 변경하기
list.set(1,5);

//list의 모든 값 삭제 => 리스트 초기화
list.clear();

//list에서 index 1에 존재하는 값 제거
list.remove(1);
//list에서 1이라는 값 제거
list.remove((Integer)1);

//list의 크기 구하기
list.size();

//list에서 index i에 해당하는 값 가져오기
list.get(i);

//list에서 값(3)이 있는지 알려줌
list.contains(3);

//list에서 값(3)이 있는지 확인하고 index값 반환(없으면 -1 반환)
list.indexOf(3);
```

<br>
#### 참고 사이트
<https://crazykim2.tistory.com/558>

### Arrays.sort()

배열을 정렬해주는 함수
ArrayList를 정렬하기 위해서는 Arrays 대신 Collections를 이용해야 한다.
#### 관련 함수
```java
import java.util.Arrays;

int arr[] = {4,23,33,15,17,19};

//arr를 오름차순 정렬
Arrays.sort(arr);

//arr를 내림차순 정렬
Arrays.sort(arr, Collections.reverseOrder());
```

<br>
#### 참고 사이트
<https://coding-factory.tistory.com/549>