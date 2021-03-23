---
layout: post
title: 2021/03/23_Algorithm
subtitle: Algorithm
tags: [Algorithm]
author: Heeyeon Jeong
comments: true
---

<br>

# 📌 1. 문제

<br>

##### 차량 10부제

<br>

서울시는 6월 1일부터 교통 혼잡을 막기 위해서 자동차 10부제를 시행한다. 자동차 10부제는
자동차 번호의 일의 자리 숫자와 날짜의 일의 자리 숫자가 일치하면 해당 자동차의 운행을 금
지하는 것이다. 예를 들어, 자동차 번호의 일의 자리 숫자가 7이면 7일, 17일, 27일에 운행하
지 못한다. 또한, 자동차 번호의 일의 자리 숫자가 0이면 10일, 20일, 30일에 운행하지 못한
다.

<br>

여러분들은 일일 경찰관이 되어 10부제를 위반하는 자동차의 대수를 세는 봉사활동을 하려고
한다. 날짜의 일의 자리 숫자가 주어지고 7대의 자동차 번호의 끝 두 자리 수가 주어졌을 때
위반하는 자동차의 대수를 출력하는 프로그램을 작성하세요.

<br>

|         입력예제         | 출력예제 |
| :----------------------: | :------: |
| 3,[23,25,11,47,53,17,35] |    3     |

<br>

# ✍ 풀이

```javascript
function solution(day, arr) {
  let answer = 0;
  for (let i = 0; i < arr.length; i++) {
    if (day.toString() === arr[i].toString().split("")[1]) {
      answer++;
    }
  }
  return answer;
}
```

# 👍 Best

```javascript
function solution(arr) {
  let answer = 0;
  for (let i of arr) {
    if (i % 10 === day) answer++;
  }
  return answer;
}
```

<br>

- 간단하게 풀기.. 1차원적으로 생각하지 말기..

<br>

# 📌 2. 문제

<br>

##### 일곱 난쟁이

<br>

왕비를 피해 일곱 난쟁이들과 함께 평화롭게 생활하고 있던 백설공주에게 위기가 찾아왔다.
일과를 마치고 돌아온 난쟁이가 일곱 명이 아닌 아홉 명이었던 것이다.
아홉 명의 난쟁이는 모두 자신이 "백설 공주와 일곱 난쟁이"의 주인공이라고 주장했다. 뛰어난
수학적 직관력을 가지고 있던 백설공주는, 다행스럽게도 일곱 난쟁이의 키의 합이 100이 됨을
기억해 냈다.
아홉 난쟁이의 키가 주어졌을 때, 백설공주를 도와 일곱 난쟁이를 찾는 프로그램을 작성하시
오.

<br>

아홉 개의 줄에 걸쳐 난쟁이들의 키가 주어진다. 주어지는 키는 100을 넘지 않는 자연수이며,
아홉 난쟁이의 키는 모두 다르며, 가능한 정답이 여러 가지인 경우에는 아무거나 출력한다.

<br>

|         입력예제         |      출력예제      |
| :----------------------: | :----------------: |
| 20 7 23 19 10 15 25 8 13 | 20 7 23 19 10 8 13 |

<br>

# ✍ 풀이

```javascript
function solution(arr) {
  let answer = arr;
  let sum = arr.reduce((a, b) => a + b);
  console.log(sum);
  for (let i = 0; i < arr.length - 1; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      if (sum - (arr[i] + arr[j]) === 100) {
        arr.splice(i, 1);
        arr.splice(j - 1, 1);
      }
    }
  }
  return answer;
}
```

<br>

- 합이 100이라는 것은 잘못 된 두 요소가 빠졌을 때 합이 100이 나온다는 점
- 이중 for문 작성할 때 i와 j가 겹치지 않게 j는 i+1로 기준을 잡기
- 이중 for문 내에서 splice 사용시, index가 바뀔 수 있기 때문에 염두하고 splice사용, 뒤에 있는 index를 먼저 제거하거나 / i 제거 후 j-1로 인덱스를 바꿔줘야 함

<br>

# 📌 3. 문제

<br>

##### 대문자 찾기

<br>

한개의 문자열을 입력받아 해당 문자열에 알파벳 대문자가 몇 개 있는지 알아내는 프로그램
을 작성하세요.

<br>

|    입력예제     | 출력예제 |
| :-------------: | :------: |
| "KoreaTimeGood" |    3     |

<br>

# ✍ 풀이

```javascript
function solution(s) {
  let answer = 0;
  for (let x of s) {
    if (x === x.toUpperCase()) {
      answer++;
    }
  }
  return answer;
}
```

<br>

- 이 문제는 난이도가 있는 문제는 아니었지만, charCodeAt에 대해 새로 배워서 남겨두고 싶었다.
- 우선 일반적으로 **toUpperCase**를 사용하면 간단하게 풀 수 있는 문제이다. x를 toUpperCase를 사용하면 기존의 x를 변화시키지 않고 대문자로 바꿀 수 있어서 비교하여 찾을 수 있다.
- **charCodeAt는 문자를 숫자로 변환해주는데 대문자는 65~90까지, 소문자는 97~122까지 해당된다.**
