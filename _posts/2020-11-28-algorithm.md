---
layout: post
title: 2020/11/28_Algorithm
subtitle: Algorithm, Codewars
tags: [Algorithm, Codewars]
author: Heeyeon Jeong
comments: False
---

<br>

# 📌 1. 문제

<br>

##### [Codewars, 6kyu] Playing with digits

<br>

Some numbers have funny properties. For example:

<br>

89 --> 8¹ + 9² = 89 \* 1<br>
695 --> 6² + 9³ + 5⁴= 1390 = 695 \* 2<br>
46288 --> 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 \* 51<br>

<br>

Given a positive integer n written as abcd... (a, b, c, d... being digits) and a positive integer p

we want to find a positive integer k, if it exists, such as the sum of the digits of n taken to the successive powers of p is equal to k \* n.
In other words:

Is there an integer k such as : (a ^ p + b ^ (p+1) + c ^(p+2) + d ^ (p+3) + ...) = n \* k

If it is the case we will return k, if not return -1.

<br>

Note: n and p will always be given as strictly positive integers.

<br>

```console
digPow(89, 1) should return 1 since 8¹ + 9² = 89 = 89 * 1
digPow(92, 1) should return -1 since there is no k such as 9¹ + 2² equals 92 * k
digPow(695, 2) should return 2 since 6² + 9³ + 5⁴= 1390 = 695 * 2
digPow(46288, 3) should return 51 since 4³ + 6⁴+ 2⁵ + 8⁶ + 8⁷ = 2360688 = 46288 * 51
```

<br>

# ✍ 풀이

```javascript
function digPow(n, p) {
  let result = 0;
  let arr = n.toString().split("");
  for (let i = 0; i < arr.length; i++) {
    result = Math.pow(arr[i], p + i) + result;
  }
  return result % n ? -1 : result / n;
}
```

<br>

- `Math.pow`로 제곱근 계산을 했다. `**` 연산자도 가능..! 삼항연산자 사용해서 코드 길이를 쵸큼..줄였지만 다음부터는 `result = Math.pow(arr[i], p + i) + result;` 대신 `result += Math.pow(arr[i], p + i);` 사용할 것..

<br>

---

<br>

# 📌 2. 문제

<br>

##### [Codewars, 7kyu] Number of People in the Bus

<br>

There is a bus moving in the city, and it takes and drop some people in each bus stop.

You are provided with a list (or array) of integer arrays (or tuples). Each integer array has two items which represent number of people get into bus (The first item) and number of people get off the bus (The second item) in a bus stop.

Your task is to return number of people who are still in the bus after the last bus station (after the last array). Even though it is the last bus stop, the bus is not empty and some people are still in the bus, and they are probably sleeping there :D

Take a look on the test cases.

Please keep in mind that the test cases ensure that the number of people in the bus is always >= 0. So the return integer can't be negative.

The second value in the first integer array is 0, since the bus is empty in the first bus stop.

<br>

```console
Test.assertEquals(number([[10,0],[3,5],[5,8]]),5);
Test.assertEquals(number([[3,0],[9,1],[4,10],[12,2],[6,1],[7,10]]),17);
Test.assertEquals(number([[3,0],[9,1],[4,8],[12,2],[6,1],[7,8]]),21);
```

<br>

# ✍ 풀이

```javascript
var number = function (busStops) {
  let a = 0;
  busStops.forEach((arr) => {
    a = arr[0] - arr[1] + a;
  });
  return a;
};
```

# 👍 Best

```javascript
const number = (busStops) =>
  busStops.reduce((rem, [on, off]) => rem + on - off, 0);
```

<br>

- 내 풀이보고 best 풀이보니까 훨씬 깔끔.. 모든 요소 전부 더할 때는 `forEach`말고 `reduce`함수 사용하자..
