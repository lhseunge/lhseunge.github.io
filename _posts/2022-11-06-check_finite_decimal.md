---
title: "[프로그래머스] 유한소수 판별하기"
date: 2022-11-06 23:56:00 +0900
last_modified_at: 2022-11-06 23:56:00 +0900

categories:
  - algorithm

tags: 
  - programmers

toc: true
toc_sticky: true

header: 
  teaser: /assets/images/github-page.jpeg

sidebar:
  nav: "docs"
---

# 배열 두 배 만들기
문제 설명
소수점 아래 숫자가 계속되지 않고 유한개인 소수를 유한소수라고 합니다. 분수를 소수로 고칠 때 유한소수로 나타낼 수 있는 분수인지 판별하려고 합니다. 유한소수가 되기 위한 분수의 조건은 다음과 같습니다.

- 기약분수로 나타내었을 때, 분모의 소인수가 2와 5만 존재해야 합니다.

두 정수 a와 b가 매개변수로 주어질 때, a/b가 유한소수이면 1을, 무한소수라면 2를 return하도록 solution 함수를 완성해주세요.

## 제한사항
- a, b는 정수

- 0 < a ≤ 1,000

- 0 < b ≤ 1,000

## 입출력 예
|a|b|result|
|---|---|---|
|7|20|1|
|11|22|1|
|12|21|2|

### 입출력 예 #1

- [1, 2, 3, 4, 5]의 각 원소에 두배를 한 배열 [2, 4, 6, 8, 10]을 return합니다.
### 입출력 예 #2

- [1, 2, 100, -99, 1, 2, 3]의 각 원소에 두배를 한 배열 [2, 4, 200, -198, 2, 4, 6]을 return합니다.

## 나의 풀이
```
import java.util.*;

class Solution {
    public int[] solution(int[] numbers) {
        int[] answer = numbers;
        for(int i = 0 ; i < answer.length; i++ ){

            answer[i] *= 2;
        }

        return answer;
    }
}
```
