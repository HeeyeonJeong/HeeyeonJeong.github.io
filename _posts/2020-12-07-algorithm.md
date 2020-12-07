---
layout: post
title: 2020/12/07_Algorithm
subtitle: Algorithm, Programmers
tags: [Algorithm, Programmers]
author: Heeyeon Jeong
comments: true
---

<br>

# 📌 1. 문제

<br>

##### [Programmers, Level1] 두 정수 사이의 합

<br>

두 정수 a, b가 주어졌을 때 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수, solution을 완성하세요.
예를 들어 a = 3, b = 5인 경우, 3 + 4 + 5 = 12이므로 12를 리턴합니다.

<br>

제한 조건<br>
a와 b가 같은 경우는 둘 중 아무 수나 리턴하세요.<br>
a와 b는 -10,000,000 이상 10,000,000 이하인 정수입니다.<br>
a와 b의 대소관계는 정해져있지 않습니다.

<br>

|  a  |  b  | return |
| :-: | :-: | :----: |
|  3  |  5  |   12   |
|  3  |  3  |   3    |

<br>

# ✍ 풀이

```javascript
function solution(a, b) {
  let num = a + b;
  const arr = [a, b].sort((a, b) => a - b);
  let i = 1;
  while (i > 0) {
    if (arr[1] - arr[0] === i || arr[1] - arr[0] === 0) {
      break;
    }
    num = arr[1] - i + num;
    i++;
  }
  return a === b ? a : num;
}
```

# 👍 Best

```javascript
function adder(a, b) {
  var result = 0;
  return ((a + b) * (Math.abs(b - a) + 1)) / 2;
}
```

<br>

- 내 풀이가 너무 장황하고 1차원적이라고 생각하면서 제출하긴 했는데, best 풀이보고 감탄을 했다,,, (best풀이의 댓글에서도 다들 감탄..) 양쪽의 숫자를 같이 뽑아서 계산하는 방법은 생각을 못했다..
  `Math.abs() 절댓값 반환` 기억해서 나중에 써먹어야지..^^
