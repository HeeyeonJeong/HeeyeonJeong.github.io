---
layout: post
title: 2021/04/02_Algorithm
subtitle: Algorithm
tags: [Algorithm, leetcode]
author: Heeyeon Jeong
comments: true
---

<br>

# 📌 1. 문제

<br>

##### 121. Best Time to Buy and Sell Stock

<br>

사고 팔았을 때 가장 큰 이익 찾기

<br>

Input: prices = [7,1,5,3,6,4]<br>

Output: 5<br>

Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

<br>

- [leetcode link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

<br>

# ✍ 풀이

#### 1차 시도

```javascript
var maxProfit = function (prices) {
  let max = 0;
  for (let i = 0; i < prices.length; i++) {
    for (let j = i + 1; j < prices.length; j++) {
      if (prices[j] - prices[i] > max) {
        max = prices[j] - prices[i];
      }
    }
  }
  return max;
};
```

<br>

- 단순히 이중 for문을 돌려서 max값을 찾으면 될 줄 알았다. 결과는 맞지만 시간초과로 다른 방식을 생각해야한다.

<br>

#### 2차 시도

```javascript
var maxProfit = function (prices) {
  let min = prices[0];
  let max = 0;
  for (let i = 1; i < prices.length; i++) {
    if (prices[i] < min) min = prices[i];
    else if (prices[i] - min > max) {
      max = prices[i] - min;
    }
  }
  return max;
};
```

<br>

- for문을 두번 돌리지 않고 for문이 한번 돌때마다 최솟값과 최댓값, 결과 값을 모두 갱신 시켜주는 방법을 사용했다.

<br>

# 📌 2. 문제

<br>

##### 20. Valid Parentheses

<br>

올바른 괄호인지 판별하기

<br>

Input: s = "(]"<br>
Output: false

<br>

Input: s = "{[]}"<br>
Output: true

<br>

- [leetcode link](https://leetcode.com/problems/valid-parentheses/)

<br>

# ✍ 풀이

#### 1차 시도

```javascript
var isValid = function (s) {
  let answer = true;
  let stack = [];

  for (let i = 0; i < s.length; i++) {
    if (s[i] === "(" || s[i] === "[" || s[i] === "{") {
      stack.push(s[i]);
    } else {
      if (stack.length === 0) answer = false;
      if (s[i] === ")" && stack[stack.length - 1] === "(") {
        stack.pop();
      } else if (s[i] === "]" && stack[stack.length - 1] === "[") {
        stack.pop();
      } else if (s[i] === "}" && stack[stack.length - 1] === "{") {
        stack.pop();
      } else {
        answer = false;
      }
    }
  }

  if (stack.length !== 0) answer = false;
  return answer;
};
```

<br>

- stack 자료구조를 사용했다. 여는 괄호일 때는 스택에 push하고 닫는 괄호 일때는 스택의 마지막 요소가 닫는 괄호의 짝인지 확인한 후, 맞다면 마지막 요소는 pop시키는 코드를 작성했다.
