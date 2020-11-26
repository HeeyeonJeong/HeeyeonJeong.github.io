---
layout: post
title: 2020/11/26_Algorithm
subtitle: Algorithm, Codewars
tags: [Algorithm, Codewars]
author: Heeyeon Jeong
comments: False
---

<br>

# 📌 1. 문제

<br>

##### [Codewars, 8kyu] Century From Year

<br>

The first century spans from the year 1 up to and including the year 100, The second - from the year 101 up to and including the year 200, etc.

```console
Task :
Given a year, return the century it is in.

Input , Output Examples ::
centuryFromYear(1705) returns (18)
centuryFromYear(1900) returns (19)
centuryFromYear(1601) returns (17)
centuryFromYear(2000) returns (20)
Hope you enjoy it .. Awaiting for Best Practice Codes

Enjoy Learning !!!
```

<br>

# ✍ 풀이

```javascript
function century(year) {
  let result = year / 100;
  return Math.ceil(result);
}
```

<br>

- 몇세기인지 확인하는 함수를 작성하는 문제인듯.. 100을 나눠 나머지가 나오면 `ceil` 올림하는 함수를 작성

<br>

---

<br>

# 📌 2. 문제

<br>

##### [Codewars, 7kyu] Find the divisors!

<br>

Create a function named divisors/Divisors that takes an integer n > 1 and returns an array with all of the integer's divisors(except for 1 and the number itself), from smallest to largest. If the number is prime return the string '(integer) is prime' (null in C#) (use Either String a in Haskell and Result<Vec<u32>, String> in Rust).

```console
Example:
divisors(12); // should return [2,3,4,6]
divisors(25); // should return [5]
divisors(13); // should return "13 is prime"
```

<br>

# ✍ 풀이

```javascript
function divisors(integer) {
  let result = [];
  for (let i = 2; i < integer; i++) {
    if (integer % i === 0) {
      result.push(i);
    }
  }
  if (result.length === 0) {
    return `${integer} is prime`;
  }
  return result;
}
```

<br>

- 1과 integer은 제외한, integer의 약수를 찾는 문제라고 접근했다.. 2와 integer의 사이의 숫자를 반복문을 돌려서 나눴을 때 나머지가 0이면 배열에 `push`

<br>

---

<br>

# 📌 3. 문제

<br>

##### [Codewars, 6kyu] Multiples of 3 or 5

<br>

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Finish the solution so that it returns the sum of all the multiples of 3 or 5 below the number passed in.

Note: If the number is a multiple of both 3 and 5, only count it once. Also, if a number is negative, return 0(for languages that do have them)

<br>

# ✍ 풀이

```javascript
function solution(number) {
  let result = [];
  for (let i = 0; i < number; i++) {
    if (i % 3 === 0 || i % 5 === 0) {
      result.push(i);
    }
  }
  const result2 = result.reduce(function (prev, curr) {
    return prev + curr;
  }, 0);
  return result2;
}
```

<br>

- 배열에 있는 모든 수를 더하기 위해 `reduce`를 사용했다. 그런데 추천풀이에서는 result를 그냥 0이라는 변수로 두고 반복문이 돌때 마다 `result+=i` 하나씩 더해지는 코드가 사용됐다..^^^ 괜히 더 어렵게 생각했네..^^
