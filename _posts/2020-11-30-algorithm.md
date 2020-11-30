---
layout: post
title: 2020/11/30_Algorithm
subtitle: Algorithm, Codewars
tags: [Algorithm, Codewars]
author: Heeyeon Jeong
comments: False
---

<br>

# 📌 1. 문제

<br>

##### [Codewars, 7kyu] Get the Middle Character

<br>

You are going to be given a word. Your job is to return the middle character of the word. If the word's length is odd, return the middle character. If the word's length is even, return the middle 2 characters.

<br>

```console
Kata.getMiddle("test") should return "es"
Kata.getMiddle("testing") should return "t"
Kata.getMiddle("middle") should return "dd"
Kata.getMiddle("A") should return "A"
```

<br>

# ✍ 풀이

```javascript
function getMiddle(s) {
  const str = s.split("");
  const count = str.length;
  if (count % 2) {
    return str[Math.floor(count / 2)];
  } else {
    return str[count / 2 - 1] + str[count / 2];
  }
}
```

# 👍 Best

```javascript
function getMiddle(s) {
  return s.substr(Math.ceil(s.length / 2 - 1), s.length % 2 === 0 ? 2 : 1);
}
```

<br>

- 가운데 문자열 찾기 문제로, best풀이에서 사용한 `substr()` 메서드는 문자열에서 특정 위치에서 시작하여 특정 문자 수 만큼의 문자들을 반환하는 메서드다. 그런데 MDN문서에서 해당 메서드는 사용하지 말 것을 권장하는 부록이 있어서 `substr()`는 안쓰는 걸루.. 삼항연산자는 사용해서 코드 간결하게 만들기
