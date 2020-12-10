---
layout: post
title: 2020/12/10_Algorithm
subtitle: Algorithm, Programmers
tags: [Algorithm, Programmers]
author: Heeyeon Jeong
comments: true
---

<br>

# 📌 1. 문제

<br>

##### [Programmers, Level1] 핸드폰 번호 가리기

<br>

프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.
전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 \*으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.<br>

<br>

제한 조건<br>
s는 길이 4 이상, 20이하인 문자열입니다.<br>

<br>

| phone_number  |        return        |
| :-----------: | :------------------: |
| "01033334444" | "\*\*\*\*\*\*\*4444" |
|  "027778888"  |  "\*\*\*\*\*\*8888"  |

<br>

# ✍ 풀이

```javascript
function solution(phone_number) {
  const num = phone_number.length - 4;
  let arr = [phone_number.slice(phone_number.length - 4, phone_number.length)];
  for (let i = 0; i < num; i++) {
    arr.unshift("*");
  }
  return arr.join("");
}
```

# 👍 Best

```javascript
function hide_numbers(s) {
  var result = "*".repeat(s.length - 4) + s.slice(-4);
  return result;
}
```

<br>

- 마지막 index-4번째 ~ 마지막 index까지 먼저 배열에 넣어두고 for문을 돌리면서 배열의 맨 앞으로 "\*"이 들어가게 `unshift`메소드를 사용했다.
- Best 코드는 `repeat`을 사용하여 "\*"이 반복되게 하였다. 같은 문자열이니까 `repeat` 사용할 껄 괜히 for문으로 돌렸다는 생각..
