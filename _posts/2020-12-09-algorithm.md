---
layout: post
title: 2020/12/09_Algorithm
subtitle: Algorithm, Programmers
tags: [Algorithm, Programmers]
author: Heeyeon Jeong
comments: true
---

<br>

# 📌 1. 문제

<br>

##### [Programmers, Level1] 수박수박수박수박수?

<br>
길이가 n이고, 수박수박수박수....와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 수박수박을 리턴하고 3이라면 수박수를 리턴하면 됩니다.

<br>

제한 조건 <br>
n은 길이 10,000이하인 자연수입니다.

<br>

|  n  |   return   |
| :-: | :--------: |
|  3  |  "수박수"  |
|  4  | "수박수박" |

<br>

# ✍ 풀이

```javascript
function solution(n) {
  let arr = [];
  for (let i = 0; i < n; i++) {
    i % 2 ? arr.push("박") : arr.push("수");
  }
  const answer = arr.join("");
  return answer;
}
```

<br>

- 다른 풀이에서는 `repeat` 메소드를 사용한 사람도 꽤 있었다. <br>
  <b>`str.repeat(count)` : 주어진 횟수(count)만큼 반복해 붙이 새로운 문자열이다.(MDN)</b> <br>
  (MDN을 보니 IE에서는 호환이 안되네..^^하하..) <br>
  (+) 번외로 누가 수박수박수박을 길게 작성해서 변수에 할당하고 substring으로 문자열을 자른걸보고 웃겼..ㅋㅋ)

<br>

# 📌 2. 문제

<br>

##### [Programmers, Level1] 문자열 내 p와 y의 개수

<br>

대문자와 소문자가 섞여있는 문자열 s가 주어집니다. s에 'p'의 개수와 'y'의 개수를 비교해 같으면 True, 다르면 False를 return 하는 solution를 완성하세요. 'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴합니다. 단, 개수를 비교할 때 대문자와 소문자는 구별하지 않습니다.<br>

<br>

예를 들어 s가 pPoooyY면 true를 return하고 Pyy라면 false를 return합니다.

<br>

제한사항<br>
문자열 s의 길이 : 50 이하의 자연수<br>
문자열 s는 알파벳으로만 이루어져 있습니다.<br>

<br>

|     s     | answer |
| :-------: | :----: |
| "pPoooyY" |  true  |
|   "Pyy"   | false  |

<br>

# ✍ 풀이

```javascript
function solution(s) {
  const arr = s.toUpperCase().split("");
  const pArr = arr.filter((item) => {
    return item === "P";
  });
  const yArr = arr.filter((item) => {
    return item === "Y";
  });
  return pArr.length - yArr.length === 0;
}
```

<br>

# 👍 Best - 1

```javascript
function numPY(s) {
  return (
    s.toUpperCase().split("P").length === s.toUpperCase().split("Y").length
  );
}
```

# 👍 Best - 2

```javascript
function numPY(s) {
  return s.match(/p/gi).length == s.match(/y/gi).length;
}
```

<br>

- 코드를 제출하면서도 통과는 되겠지만, 진짜 별로라고 생각했다,,,^^ 우선 나는 원하는 요소의 개수를 찾는 메소드를 생각해봤는데 없어서.. `filter` 메소드로 조건에 만족하는 새배열을 만들어 개수를 비교하는 코드를 짰다.<br>
  - best-1 코드는 `split`으로 문자를 나눌 때, 해당 문자열로 나눠서 배열의 개수를 비교했다. 나는 p와 y의 정확한 개수만 비교하려고 했는데 `split`으로 나눠진 배열의 개수를 구하는 것도 새로운 접근이었던 것 같다. (+ 내 코드와 비교했을 때, 내 풀이의 `filter`는 정말 필요없는 메소드를 썼다고 생각했다..)
  - best-2 에서는 `match` 메소드를 사용했다. 이 메소드는 처음봤다.<br>
    <b>`match` : 문자열이 정규식과 매치되는 부분을 검색합니다.(MDN)<br>
    i는 대소문자 상관없이 g는 전부 찾으라는 플래그. → [regular expression - MDN 참고](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D)</b>
