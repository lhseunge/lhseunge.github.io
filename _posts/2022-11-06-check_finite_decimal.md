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

- 분수 7/20은 기약분수 입니다. 분모 20의 소인수가 2, 5 이기 때문에 유한소수입니다. 따라서 1을 return합니다.
### 입출력 예 #2

- 분수 11/22는 기약분수로 나타내면 1/2 입니다. 분모 2는 소인수가 2 뿐이기 때문에 유한소수 입니다. 따라서 1을 return합니다.
### 입출력 예 #2

- 분수 12/21는 기약분수로 나타내면 4/7 입니다. 분모 7은 소인수가 7 이므로 무한소수입니다. 따라서 2를 return합니다.


### Hint

- 분자와 분모의 최대공약수로 약분하면 기약분수를 만들 수 있습니다.

- 정수도 유한소수로 분류합니다.

## 나의 풀이
```
import java.util.*;
import java.math.*;
class Solution {
    public int solution(int a, int b) {

        int gcd = BigInteger.valueOf(a).gcd(BigInteger.valueOf(b)).intValue();

        b /= gcd;

        if (b == 2 || b == 5 || b ==  1) {
            return 1;

        } else if (b == 3) {
            return 2;

        }

        if (a % b == 0) {
            return 1;
        }

        int answer = 1;

        for (int i = 2; i <= b; i++) {
            while(b % i == 0) {
                
                if(!( i == 2 || i == 5 )) {
                    return 2;
                }
                
                b /= i;

            }
           
        }
        
        return answer;
    }

}
```
## 모범 풀이
```
class Solution {
    public int solution(int a, int b) {
        int gcd = findGCD(a, b);
        b = b / gcd;

        for (int i = 2; i <= b; i++) {
            while (b % i == 0) {
                if (i != 2 && i != 5) {
                    return 2;
                }

                b /= i;
            }

            if (b == 1) {
                break;
            }
        }

        return 1;
    }

    public int findGCD(int a, int b) {
        if (a % b == 0) {
            return b;
        }

        return findGCD(b, a % b);
    }
}
```

## 모범 풀이
```
class Solution {
    public int solution(int a, int b) {
        /*
          문제 중 파라미터 a, b 의 최대 값은 1000이므로 
          분자에 1000을 곱한 후 b와 나누어 떨어진다면 유한소수, 떨어지지 않는다면 무한소수라고 볼 수 있다.
          
          알고리즘 문제만 제대로 읽고 요점을 파악한다면, 문제를 쉽게 해결할 수 있을듯
        */
        int answer = ((a*1000)%b == 0) ? 1 : 2;
        return answer;
    }
}
```
