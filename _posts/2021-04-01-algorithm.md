---
layout: post
title: 2021/04/01_Algorithm
subtitle: Algorithm
tags: [Algorithm, hackerrank, programmers]
author: Heeyeon Jeong
comments: true
---

<br>

# 📌 1. 문제

<br>

##### Sorting. Bubble sort

<br>

버블 정렬 알고리즘을 사용하여 오름차순으로 배열을 정렬하고,count하기

<br>

3 2 1

- [hackerrank - Bubble sort](https://www.hackerrank.com/challenges/ctci-bubble-sort/problem)

<br>

# ✍ 풀이

```javascript
function countSwaps(a) {
  let cnt = 0;
  let answer = a;
  for (let i = 0; i < a.length - 1; i++) {
    for (let j = 0; j < a.length - i - 1; j++) {
      if (a[j] > a[j + 1]) {
        cnt++;
        [a[j], a[j + 1]] = [a[j + 1], a[j]];
      }
    }
  }
  console.log(`Array is sorted in ${cnt} swaps.`);
  console.log(`First Element: ${answer[0]}`);
  console.log(`Last Element: ${answer[answer.length - 1]}`);
}
```

<br>

# 📌 2. 문제

<br>

##### 정렬. 가장 큰 수

<br>

0 또는 양의 정수가 주어졌을 때, 정수를 이어 붙여 만들 수 있는 가장 큰 수를 알아내 주세요.

<br>

예를 들어, 주어진 정수가 [6, 10, 2]라면 [6102, 6210, 1062, 1026, 2610, 2106]를 만들 수 있고, 이중 가장 큰 수는 6210입니다.

<br>

0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 바꾸어 return 하도록 solution 함수를 작성해주세요.

<br>

|  numbers   | return |
| :--------: | :----: |
| [6, 10, 2] | "6210" |

<br>

# ✍ 풀이

```javascript
function solution(numbers) {
  let arr = numbers.map((num) => num.toString());
  arr.sort((a, b) => b + a - (a + b)).join("");
  return arr[0] === "0" ? "0" : arr.join("");
}
```
