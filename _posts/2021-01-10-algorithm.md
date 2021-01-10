---
layout: post
title: 2021/01/10_Algorithm
subtitle: Algorithm, Programmers
tags: [Algorithm, Programmers]
author: Heeyeon Jeong
comments: true
---

<br>

# 📌 1. 문제

<br>

##### [Programmers, Level1] 같은 숫자는 싫어

<br>

배열 arr가 주어집니다. 배열 arr의 각 원소는 숫자 0부터 9까지로 이루어져 있습니다. 이때, 배열 arr에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려고 합니다. 단, 제거된 후 남은 수들을 반환할 때는 배열 arr의 원소들의 순서를 유지해야 합니다. 예를 들면,

<br>

arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return 합니다.
arr = [4, 4, 4, 3, 3] 이면 [4, 3] 을 return 합니다.
배열 arr에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수를 완성해 주세요.

<br>

제한사항<br>
배열 arr의 크기 : 1,000,000 이하의 자연수<br>
배열 arr의 원소의 크기 : 0보다 크거나 같고 9보다 작거나 같은 정수

<br>

|       arr       |  answer   |
| :-------------: | :-------: |
| [1,1,3,3,0,1,1] | [1,3,0,1] |
|   [4,4,4,3,3]   |   [4,3]   |

<br>

# ✍ 풀이

```javascript
function solution(arr) {
  var answer = [];
  for (let i = 0; i < arr.length; i++) {
    if (answer[answer.length - 1] !== arr[i]) answer.push(arr[i]);
  }
  return answer;
}
```

# 👍 Best

```javascript
function solution(arr) {
  return arr.filter((val, index) => val != arr[index + 1]);
}
```

<br>

- 빈 배열을 만들고 빈 배열의 마지막 인덱스의 요소가 새로 들어올 요소와 같다면 push되지 않는 코드를 만들었다.
