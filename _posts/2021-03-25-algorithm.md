---
layout: post
title: 2021/03/25_Algorithm
subtitle: Algorithm
tags: [Algorithm, leetcode]
author: Heeyeon Jeong
comments: true
---

<br>

# 📌 1. 문제

<br>

##### 27. Remove Element

<br>

Given an array nums and a value val, remove all instances of that value in-place and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

Clarification:

Confused why the returned value is an integer but your answer is an array?

Note that the input array is passed in by reference, which means a modification to the input array will be known to the caller as well.

Internally you can think of this:

<br>

Input: nums = [0,1,2,2,3,0,4,2], val = 2
Output: 5, nums = [0,1,4,0,3]
Explanation: Your function should return length = 5, with the first five elements of nums containing 0, 1, 3, 0, and 4. Note that the order of those five elements can be arbitrary. It doesn't matter what values are set beyond the returned length.

<br>

# ✍ 풀이

```javascript
var removeElement = function (nums, val) {
  for (let i = nums.length - 1; i >= 0; i--) {
    if (nums[i] === val) nums.splice(i, 1);
  }
  return nums.length;
};
```

<br>

- splice를 사용할때는 for문을 되도록 뒤에서 돌려야겠다.. 자꾸 앞에서 돌리다가 index가 어긋나는 듯 싶다..

<br>

# 📌 2. 문제

<br>

##### 125. Valid Palindrome (회문 문자열)

<br>

Given a string s, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

<br>

Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.

<br>

- [leetcode Link](https://leetcode.com/problems/valid-palindrome/)

<br>

# ✍ 풀이

```javascript
var isPalindrome = function (s) {
  let answer = true;
  let lower = s.toLowerCase().replace(/[^a-z0-9+]/g, "");
  let num = lower.length / 2;
  for (let i = 0; i < num; i++) {
    if (lower[i] !== lower[lower.length - i - 1]) answer = false;
  }
  return answer;
};
```

<br>

- 회문 문자 확인시 가장 먼저 남겨야 할 문자가 어떤건지 확인 후 에 정규식으로 작성했다. (최근에 정규표현식을 공부하고 있는데 훨씬 편하다.) 문제에서는 영,숫자를 모두 포함해야한다고 해서 **toLowerCase**로 전체 문자열을 소문자로 만들고, **replace(/[^a-z0-9+]/g,"")**로 영,숫자 외 문자는 제거 했다.
- 전체 문자열의 반만 for문으로 돌려서 양쪽 끝의 index를 뽑아서 같은 문자인지 확인하는 방식으로 코드를 작성했다.
