---
layout: post
title: 2020/12/27_Algorithm
subtitle: Algorithm, Programmers
tags: [Algorithm, Programmers]
author: Heeyeon Jeong
comments: true
---

<br>

# 📌 1. 문제

<br>

##### [Programmers, Level1] 해시 | 완주하지 못한 선수

<br>

수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

<br>

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

<br>
<b>제한사항</b><br>

마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.<br>
completion의 길이는 participant의 길이보다 1 작습니다.<br>
참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.<br>
참가자 중에는 동명이인이 있을 수 있습니다.<br>

<br>

|              participant              |         completion          | return   |
| :-----------------------------------: | :-------------------------: | -------- |
|        ["leo", "kiki", "eden"]        |      ["eden", "kiki"]       | "leo"    |
| ["mislav", "stanko", "mislav", "ana"] | ["stanko", "ana", "mislav"] | "mislav" |

<br>

# ✍ 풀이

##### 1차 시도 - 정확성 통과 ⭕, 효율성 실패 ❌

```javascript
function solution(participant, completion) {
  for (let i = 0; i < completion.length; i++) {
    let num = participant.indexOf(completion[i]);
    participant.splice(num, 1);
  }
  return participant[0];
}
```

##### 2차 시도 - 정확성 통과 ⭕, 효율성 실패 ❌

```javascript
function solution(participant, completion) {
  completion.forEach((item) => {
    participant.splice(participant.indexOf(item), 1);
  });
  return participant[0];
}
```

##### 3차 시도 - 정확성 통과 ⭕, 효율성 통과 ⭕

```javascript
function solution(participant, completion) {
    participant.sort();
    completion.sort();
    for(var i = 0; i < participant.length; i++) {
        if (participant[i] !== completion[i]) {
            return participant[i];
        }
    }
```

<br>

- 1차시도에서는 평소 풀던대로 `for문`으로 참가한 선수들과 완주한 선수 한명씩 비교하며 참가선수들을 지워나가는 코드를 짰다. 정확성은 통과했는데 효율성문제에서 통과하지 못했다.
- 2차시도에서 `for문`을 `forEach문`으로 변경하였지만 이 코드 또한 효율성에서 막혔다.
- 3차시도에서는 <b>가장 먼저 참가 선수들, 완주 선수들 모두 정렬</b>을 하고 정렬된 배열의 index끼리 다르면 바로 해당 선수가 `return`되는 코드로 작성했다. 3차 시도에서 효율성 문제가 해결 됐다! <b>굳이 1. for문을 전부 다 돌리고 2. 기존 배열을 삭제하는 코드 없이</b> 같은 index에서 서로 다른 요소가 나왔을 때 해당 요소가 바로 `return` 되는 부분에서 효율성이 높아진 것 같다.
