---
layout: post
title: 2020/12/06_Algorithm
subtitle: Algorithm, Programmers
tags: [Algorithm, Programmers]
author: Heeyeon Jeong
comments: true
---

<br>

# 📌 1. 문제

<br>

##### [Programmers, Level1] 두 개 뽑아서 더하기 (정렬)

<br>

정수 배열 numbers가 주어집니다. numbers에서 서로 다른 인덱스에 있는 두 개의 수를 뽑아 더해서 만들 수 있는 모든 수를 배열에 오름차순으로 담아 return 하도록 solution 함수를 완성해주세요.

<br>

```console
numbers
[2,1,3,4,1]
result
[2,3,4,5,6,7]
```

<br>

# ✍ 풀이

```javascript
function solution(numbers) {
  let answer = [];
  for (let i = 0; i < numbers.length; i++) {
    for (let j = i + 1; j < numbers.length; j++) {
      answer.push(numbers[i] + numbers[j]);
    }
  }
  const arr = [...new Set(answer)];
  const result = arr.sort((a, b) => a - b);
  return result;
}
```

<br>

- `const set = new Set(array)` set 객체를 이용하여 중복없는 데이터를 만들고, set객체로 중복을 제거한 후, Spread Operator, 전개연산자 `[...set]` 를 사용하여 객체를 배열로 변환했다.

<br>

# 📌 2. 문제

<br>

##### [Programmers, Level1] K번째수

<br>

배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

<br>

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면

<br>

array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
2에서 나온 배열의 3번째 숫자는 5입니다.

<br>

```console
array
[1, 5, 2, 6, 3, 7, 4]
commands
[[2, 5, 3], [4, 4, 1], [1, 7, 3]]
return
[5, 6, 3]
```

<br>

# ✍ 풀이

```javascript
function solution(array, commands) {
  let answer = [];
  for (let i = 0; i < commands.length; i++) {
    const arr = array.slice(commands[i][0] - 1, commands[i][1]);
    const result = arr.sort((a, b) => a - b);
    answer.push(result[commands[i][2] - 1]);
  }
  return answer;
}
```

<br>

# 📌 3. 문제

<br>

##### [Programmers, Level1] K번째수

<br>

단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

<br>

재한사항 <br>
s는 길이가 1 이상, 100이하인 스트링입니다.

<br>

```console
s
"a,b,c,d,e"
return
"c"

s
"a,b,c,d"
return
"b,c"

```

<br>

# ✍ 풀이

```javascript
function solution(s) {
  const arr = s.split("");
  const numbers = arr.length;
  if (numbers % 2) {
    return arr[Math.floor(numbers / 2)];
  } else {
    return arr[numbers / 2 - 1] + arr[numbers / 2];
  }
}
```

<br>

- 전에도 codewars에서 가운데 글자 가져오기 문제를 푼 적이 있는데 programmers에서도 풀게되었다..! 저번과 코드를 비교하니 또 삼항연산자 안쓰고 굳이 길게 썼네..
