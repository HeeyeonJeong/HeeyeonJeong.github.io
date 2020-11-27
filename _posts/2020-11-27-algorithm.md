---
layout: post
title: 2020/11/27_Algorithm
subtitle: Algorithm, Codewars
tags: [Algorithm, Codewars]
author: Heeyeon Jeong
comments: False
---

<br>

# 📌 1. 문제

<br>

##### [Codewars, 7kyu] Square Every Digit

<br>

Welcome. In this kata, you are asked to square every digit of a number and concatenate them.

For example, if we run 9119 through the function, 811181 will come out, because 92 is 81 and 12 is 1.

Note: The function accepts an integer and returns an integer

```console
Test.assertEquals(squareDigits(9119), 811181);
```

<br>

# ✍ 풀이

```javascript
function squareDigits(num) {
  let result = [];
  let array = num.toString().split("");
  array.forEach((item) => {
    result.push(item * item);
  });
  return parseInt(result.join(""));
}
```

<br>

- 숫자를 문자로 바꿔서 하나의 배열이 되는 변수를 만들고, `forEach`로 배열을 돌려 빈 배열 변수에 계산된 요소가 `push`되는 코드를 작성했다. 추천풀이에서는 `map`을 사용하여 빈 배열을 만들지 않고 `arrow function`으로 바로 새로운 배열을 만들어냈다. 매번 같은 메소드만 써서 문제푸는 느낌.... 다양한 방법으로 접근하자...

<br>

---

<br>

# 📌 2. 문제

<br>

##### [Codewars, 6kyu] Stop gninnipS My sdroW!

<br>

Write a function that takes in a string of one or more words, and returns the same string, but with all five or more letter words reversed (Just like the name of this Kata). Strings passed in will consist of only letters and spaces. Spaces will be included only when more than one word is present.

Examples: spinWords( "Hey fellow warriors" ) => returns "Hey wollef sroirraw" spinWords( "This is a test") => returns "This is a test" spinWords( "This is another test" )=> returns "This is rehtona test"

```console
Test.assertEquals(spinWords("Welcome"), "emocleW");
Test.assertEquals(spinWords("Hey fellow warriors"), "Hey wollef sroirraw");
Test.assertEquals(spinWords("This is a test"), "This is a test");
Test.assertEquals(spinWords("This is another test"), "This is rehtona test");
```

<br>

# ✍ 풀이

```javascript
function spinWords(item) {
  let arr = [];
  let b = item.split(" ");
  b.forEach((a) => {
    if (a.length >= 5) {
      arr.push(a.split("").reverse().join(""));
    } else {
      arr.push(a);
    }
  });
  return arr.join(" ");
}
```

<br>

- 문자의 길이가 4보다 크면 뒤집어서 `push`, 작으면 그대로 `push`되는 조건문으로 작성했다. 다음에는 삼항연산자 사용해 볼 것..!

<br>
