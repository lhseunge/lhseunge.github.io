---
title: "[프로그래머스] 배열 두 배 만들기"
date: 2022-11-05 10:19:00 +0900
last_modified_at: 2022-11-05 10:19:00 +0900

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
정수 배열 numbers가 매개변수로 주어집니다. numbers의 각 원소에 두배한 원소를 가진 배열을 return하도록 solution 함수를 완성해주세요.

## 제한사항
- -10,000 ≤ numbers의 원소 ≤ 10,000

- 1 ≤ numbers의 길이 ≤ 1,000

## 입출력 예
|numbers|result|
|---|---|
|[1, 2, 3, 4, 5]|[2, 4, 6, 8, 10]|
|[1, 2, 100, -99, 1, 2, 3]|[2, 4, 200, -198, 2, 4, 6]|

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
