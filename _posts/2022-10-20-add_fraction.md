---
title: "[프로그래머스] 분수의 덧셈"
date: 2022-11-03 01:49:00 +0900
last_modified_at: 2022-11-03 01:49:00 +0900

categories:
  - algorithm

tags: 
  - programers

toc: true
toc_sticky: true

header: 
  teaser: /assets/images/github-page.jpeg

sidebar:
  nav: "docs"
---

분수의 덧셈
문제 설명
첫 번째 분수의 분자와 분모를 뜻하는 denum1, num1, 두 번째 분수의 분자와 분모를 뜻하는 denum2, num2가 매개변수로 주어집니다. 두 분수를 더한 값을 기약 분수로 나타냈을 때 분자와 분모를 순서대로 담은 배열을 return 하도록 solution 함수를 완성해보세요.

제한사항
0 <denum1, num1, denum2, num2 < 1,000
입출력 예
denum1	num1	denum2	num2	result
1	2	3	4	[5, 4]
9	2	1	3	[29, 6]
입출력 예 설명
입출력 예 #1

1 / 2 + 3 / 4 = 5 / 4입니다. 따라서 [5, 4]를 return 합니다.
입출력 예 #2

9 / 2 + 1 / 3 = 29 / 6입니다. 따라서 [29, 6]을 return 합니다.

나의 풀이
```
import java.util.*;

class Solution {
    public int[] solution(int denum1, int num1, int denum2, int num2) {
        
        int mom = num1 * num2; 
        denum1 = denum1 * (mom/num1);
        denum2 = denum2 * (mom/num2);
        
        int son = denum1 + denum2;
        
        List<Integer> arr = new ArrayList();
        for(int i = 2; i <= son; i++) {
            if(son%i==0 && mom%i==0) {
                arr.add(i);
            }
        }
        
        if(arr.size() > 0) {
            son = son / arr.get(arr.size()-1);
            mom = mom / arr.get(arr.size()-1);
        }
        
        int[] answer = {son, mom};
        return answer;
    }
}
```

모범 풀이 
```
class Solution {
    public int GCD(int num1, int num2) {
        if (num1 % num2 == 0)
            return num2;
        return GCD(num2, num1 % num2);
    }

    public int[] solution(int denum1, int num1, int denum2, int num2) {
        int[] answer;

        denum1 *= num2;
        denum2 *= num1;

        answer = new int[]{denum1 + denum2, num1 * num2};

        int greatest_common_divisor = GCD(answer[0], answer[1]);
        answer[0] /= greatest_common_divisor;
        answer[1] /= greatest_common_divisor;

        return answer;
    }
}
```
