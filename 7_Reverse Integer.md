# 🧮 LeetCode Problem 7 - Reverse Integer


**Difficulty:** Medium    

---

## 🧾 Problem Statement  

Given a signed 32-bit integer `x`, return `x` with its digits reversed. If reversing `x` causes the value to go outside the signed 32-bit integer range `[-231, 231 - 1]`, then return `0`.

**Assume the environment does not allow you to store 64-bit integers (signed or unsigned)**.

 
---

## 💡 Example 1  
```
Input: x = 123
Output: 321

```
---

## 💡 Example 2  
```
Input: x = -123
Output: -321

```

## 💡 Example 3  
```
Input: x = 120
Output: 21

```

---

## ⚙️ Constraints   
- `-231 <= x <= 231 - 1`

## 💻 C Solution

```c

int reverse(int x){
    int rev = 0;
    const int max = 2147483647;   
    const int min = -2147483648;
    while(x != 0){
        int pop = x % 10;
        x /= 10;
        
        if (rev > max / 10 || (rev == max / 10 && pop > 7)) return 0;
        if (rev < min / 10 || (rev == min / 10 && pop < -8)) return 0;

        rev = rev * 10 + pop;
    }
    return rev;

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

1. **Initialize**

   * `rev = 0`
   * `INT_MAX = 2147483647`, `INT_MIN = -2147483648`

2. **Loop while `x != 0`**

   * `pop = x % 10` → extract last digit
   * `x = x / 10` → remove last digit

3. **Check overflow**

   * if `rev > INT_MAX/10` or (`rev == INT_MAX/10` and `pop > 7`) → return 0
   * if `rev < INT_MIN/10` or (`rev == INT_MIN/10` and `pop < -8`) → return 0

4. **Build reversed number**

   * `rev = rev * 10 + pop`

5. **Return result**

   * `return rev`

---




## 🧮 Dry Run


### 🔹 Example

`x = -123`

---

### **Initial values**

```
rev = 0
INT_MAX = 2147483647
INT_MIN = -2147483648
```

---

### **Iteration 1**

```
pop = x % 10 = -123 % 10 = -3
x = x / 10 = -123 / 10 = -12
```

Check overflow:

```
rev = 0 → safe
```

Build reversed number:

```
rev = 0 * 10 + (-3) = -3
```

---

### **Iteration 2**

```
pop = -12 % 10 = -2
x = -12 / 10 = -1
```

Check overflow:

```
rev = -3 → safe
```

Build reversed number:

```
rev = (-3) * 10 + (-2) = -32
```

---

### **Iteration 3**

```
pop = -1 % 10 = -1
x = -1 / 10 = 0
```

Check overflow:

```
rev = -32 → safe
```

Build reversed number:

```
rev = (-32) * 10 + (-1) = -321
```

---

### **End**

`x = 0` → stop.

✅ **Final result:** `rev = -321`


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
