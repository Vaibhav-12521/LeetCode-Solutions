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
char* convert(char* s, int numRows) {
    int len = 0; 
    while (s[len]) len++;
    if (numRows == 1 || numRows >= len) return s;

    char* res = (char*)malloc(len + 1);
    int cycle = 2 * numRows - 2, idx = 0;

    for (int i = 0; i < numRows; i++) {
        for (int j = i; j < len; j += cycle) {
            res[idx++] = s[j];
            if (i != 0 && i != numRows - 1) {
                int k = j + cycle - 2 * i;
                if (k < len) res[idx++] = s[k];
            }
        }
    }
    res[idx] = '\0';
    return res;
}


```

## 🐍 Python Solution

```python
class Solution:
    def reverse(self, x: int) -> int:
        max = 2**31 - 1
        min = -2**31

        sign = -1 if x < 0 else 1
        x= abs(x)
        rev = 0

        while x != 0:
            pop = x% 10

            x //= 10

            if rev > (max - pop) // 10:
                return 0
            
            rev = rev * 10 + pop

        return sign * rev

```
---




## ⚙️ Step-by-Step Solution


---




## 🧮 Dry Run



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
