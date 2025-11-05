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
    def convert(self, s: str, numRows: int) -> str:
        if numRows == 1 or numRows >= len(s):
            return s
        
        rows = [''] * numRows

        currow, step = 0, 1

        for i in s:
            rows[currow] += i
            if currow == 0:
                step = 1
            elif currow == numRows - 1:
                step = -1
            currow += step
        
        return ''.join(rows)

```
---




## ⚙️ Step-by-Step Solution
1. **Handle simple cases** — If `numRows == 1` or `numRows >= len(s)`, return `s` directly (no zigzag needed).

2. **Prepare storage** — Create a list `rows` of strings, one for each row.

3. **Track direction** — Use an index `i` for the current row and a `step` (either `1` for down or `-1` for up).

4. **Iterate through characters** — For each character in `s`, append it to `rows[i]`.

5. **Change direction** — When you hit the top (`i == 0`) or bottom (`i == numRows - 1`), reverse `step`.

6. **Move to next row** — Update `i` by adding `step`.

7. **Combine results** — Join all strings in `rows` to form the final converted string.


---




## 🧮 Dry Run

```python
s = "PAYPALISHIRING", numRows = 3
```

---

### **Initial Setup**

```python
rows = ['', '', '']  # 3 rows
currow = 0
step = 1
```

---

### **Step 1: Process characters**

**1. 'P'**

* `rows[0] += 'P'` → `rows = ['P', '', '']`
* `currow == 0`, so `step = 1`
* `currow += step` → `currow = 1`

**2. 'A'**

* `rows[1] += 'A'` → `rows = ['P', 'A', '']`
* `currow != 0` and `currow != 2`, `step` stays 1
* `currow += step` → `currow = 2`

**3. 'Y'**

* `rows[2] += 'Y'` → `rows = ['P', 'A', 'Y']`
* `currow == numRows-1`, so `step = -1`
* `currow += step` → `currow = 1`

**4. 'P'**

* `rows[1] += 'P'` → `rows = ['P', 'AP', 'Y']`
* `currow += step` → `currow = 0`

**5. 'A'**

* `rows[0] += 'A'` → `rows = ['PA', 'AP', 'Y']`
* `currow == 0`, so `step = 1`
* `currow += step` → `currow = 1`

**6. 'L'**

* `rows[1] += 'L'` → `rows = ['PA', 'APL', 'Y']`
* `currow += step` → `currow = 2`

**7. 'I'**

* `rows[2] += 'I'` → `rows = ['PA', 'APL', 'YI']`
* `currow == 2`, so `step = -1`
* `currow += step` → `currow = 1`

**8. 'S'**

* `rows[1] += 'S'` → `rows = ['PA', 'APLS', 'YI']`
* `currow += step` → `currow = 0`

**9. 'H'**

* `rows[0] += 'H'` → `rows = ['PAH', 'APLS', 'YI']`
* `currow == 0`, so `step = 1`
* `currow += step` → `currow = 1`

**10. 'I'**

* `rows[1] += 'I'` → `rows = ['PAH', 'APLSI', 'YI']`
* `currow += step` → `currow = 2`

**11. 'R'**

* `rows[2] += 'R'` → `rows = ['PAH', 'APLSI', 'YIR']`
* `currow == 2`, so `step = -1`
* `currow += step` → `currow = 1`

**12. 'I'**

* `rows[1] += 'I'` → `rows = ['PAH', 'APLSII', 'YIR']`
* `currow += step` → `currow = 0`

**13. 'N'**

* `rows[0] += 'N'` → `rows = ['PAHN', 'APLSII', 'YIR']`
* `currow == 0`, so `step = 1`
* `currow += step` → `currow = 1`

**14. 'G'**

* `rows[1] += 'G'` → `rows = ['PAHN', 'APLSIIG', 'YIR']`

---

### **Step 2: Join Rows**

```python
''.join(rows)  # "PAHNAPLSIIGYIR"
```

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
