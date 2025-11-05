# 🧮 LeetCode Problem 6 - Zigzag Conversion


**Difficulty:** Medium    

**Language Used:** C, Python 

---

## 🧾 Problem Statement  

The string `'PAYPALISHIRING'` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

```
P   A   H   N
A P L S I I G
Y   I   R
```
And then read line by line: `'PAHNAPLSIIGYIR'`

Write the code that will take a string and make this conversion given a number of rows:

`string convert(string s, int numRows);`

 
---

## 💡 Example 1  
```
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"

```
---

## 💡 Example 2  
```
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:
P     I    N
A   L S  I G
Y A   H R
P     I

```

## 💡 Example 3  
```
Input: s = "A", numRows = 1
Output: "A"

```

---

## ⚙️ Constraints   
- `1 <= s.length <= 1000`
- s consists of English letters (lower-case and upper-case), `','` and `'.'`.
- `1 <= numRows <= 1000`

## 💻 C Solution

```c


```

## 🐍 Python Solution

```python


```
---

## ⚙️ Step-by-Step Solution

### 🧩 Step-by-Step Solution

#### **Step 1: Understand what a palindrome is**

A **palindrome** is a string that reads the same from both directions, e.g. `"racecar"`, `"abba"`, `"a"`.

---

#### **Step 2: Idea — Expand around the center**

Every palindrome can be expanded from its **center**.

For example:

* `"aba"` → center is at `'b'` (odd-length)
* `"abba"` → center is between two `'b'`s (even-length)

So, for each character (and each gap between characters), we can:

1. Expand outward while `s[left] == s[right]`
2. Keep track of the longest palindrome found.

---

#### **Step 3: Check both types of palindromes**

For each index `i` in the string:

* Expand for **odd-length** palindrome → center at `i`
* Expand for **even-length** palindrome → center between `i` and `i + 1`

Take the longer of the two.

---

#### **Step 4: Keep track of the longest palindrome**

Maintain:

* `start` → starting index of the current longest palindrome
* `end` → ending index of the current longest palindrome

Whenever you find a longer palindrome, update `start` and `end`.

---

#### **Step 5: Return the substring**

At the end, return `s[start:end + 1]`.


---




## 🧮 Dry Run

`s = "babad"`

We’ll walk through **each iteration** to see how `start`, `end`, and palindrome lengths change.

---

### 🔹 Initialize

```
start = 0
end = 0
```

---

### 🔹 i = 0 → center = 'b'

Check two cases:

1. **Odd-length (expand from "b"):**

   * left = 0, right = 0 → same ('b')
   * expand → left = -1, right = 1 → stop
     → length = 1

2. **Even-length (expand between 0,1):**

   * left = 0, right = 1 → 'b' != 'a' → stop
     → length = 0

Max length = 1
Since `1 > end - start`, update:

```
start = 0
end = 0
```

→ current palindrome: `"b"`

---

### 🔹 i = 1 → center = 'a'

1. **Odd-length:**

   * left = 1, right = 1 → same ('a')
   * left = 0, right = 2 → both 'b' → same
   * left = -1, right = 3 → stop
     → length = 3 → palindrome "bab"

2. **Even-length:**

   * left = 1, right = 2 → 'a' != 'b' → stop
     → length = 0

Max length = 3
Since `3 > end - start`, update:

```
start = 0
end = 2
```

→ current palindrome: `"bab"`

---

### 🔹 i = 2 → center = 'b'

1. **Odd-length:**

   * left = 2, right = 2 → same ('b')
   * left = 1, right = 3 → both 'a' → same
   * left = 0, right = 4 → 'b' != 'd' → stop
     → length = 3 → palindrome "aba"

2. **Even-length:**

   * left = 2, right = 3 → 'b' != 'a' → stop
     → length = 0

Max length = 3
Since `3 == end - start` (no improvement), keep current:

```
start = 0
end = 2
```

→ longest still `"bab"`

---

### 🔹 i = 3 → center = 'a'

1. **Odd-length:**

   * left = 3, right = 3 → same ('a')
   * left = 2, right = 4 → 'b' != 'd' → stop
     → length = 1

2. **Even-length:**

   * left = 3, right = 4 → 'a' != 'd' → stop
     → length = 0

Max length = 1 → no update.

---

### 🔹 i = 4 → center = 'd'

1. **Odd-length:**

   * left = 4, right = 4 → same ('d')
   * left = 3, right = 5 → stop
     → length = 1

2. **Even-length:**

   * left = 4, right = 5 → stop
     → length = 0

No update.

---

### ✅ Result

After the loop:

```
start = 0
end = 2
```

→ longest palindrome substring = `s[0:3] = "bab"`

---

### 🧠 Summary Table

| i | Odd Palindrome | Even Palindrome | Longest So Far |
| - | -------------- | --------------- | -------------- |
| 0 | "b" (len 1)    | "" (len 0)      | "b"            |
| 1 | "bab" (len 3)  | "" (len 0)      | "bab"          |
| 2 | "aba" (len 3)  | "" (len 0)      | "bab"/"aba"    |
| 3 | "a" (len 1)    | "" (len 0)      | "bab"          |
| 4 | "d" (len 1)    | "" (len 0)      | "bab"          |

---

✅ **Final Output:** `"bab"` (or `"aba"`, both valid)

---

### 📎 Connect with Me

<p align="center">
  <a href="https://github.com/Vaibhav-12521" target="_blank">
    <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub Profile"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://leetcode.com/u/vaibhav125s/" target="_blank">
    <img src="https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black" alt="LeetCode Profile"/>
  </a>
  &nbsp;&nbsp;
  <a href="https://www.linkedin.com/in/vaibhavsingh125/" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn Profile"/>
  </a>
</p>

<p align="center">
  <img src="https://visitor-badge.laobi.icu/badge?page_id=second-largest-problem" alt="visitor badge"/>
</p>
