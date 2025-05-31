# 🚀 Day 14: Implement Atoi (String to Integer Conversion)

## 🧩 Problem Statement

Implement the `Atoi` function that converts a string to a 32-bit signed integer. This function mimics the behavior of the C/C++ `atoi` function.

### 📝 Problem Link:
👉 [GFG Practice Problem - Implement Atoi](https://practice.geeksforgeeks.org/problems/implement-atoi/1)

---

## ✅ Rules and Requirements:

1. **Ignore leading whitespaces**.
2. **Handle optional sign**: '+' or '-', default is positive.
3. **Read digits** until a non-digit character or end of string.
4. **Handle integer overflow/underflow**:
   - If the number is out of the signed 32-bit int range, clamp to:
     - `Integer.MAX_VALUE` = `2147483647`
     - `Integer.MIN_VALUE` = `-2147483648`
5. If no digits are found, return `0`.

---

## 🧪 Example Test Cases

| Input String              | Output         |
|---------------------------|----------------|
| `"42"`                    | `42`           |
| `"   -42"`                | `-42`          |
| `"4193 with words"`       | `4193`         |
| `"words and 987"`         | `0`            |
| `"-91283472332"`          | `-2147483648`  |
| `"0000000000012345678"`   | `12345678`     |
| `"1231231231311313"`      | `2147483647`   |
| `"-000000000000001"`      | `-1`           |
| `"+"`                     | `0`            |
| `"   +0 123"`             | `0`            |

---

## 💡 Approach

We carefully process the string step-by-step to handle all the tricky edge cases manually.

### 🔍 Steps:

1. **Trim whitespaces** at the start.
2. **Check for sign** and record it.
3. **Loop through characters** while they are digits:
   - Multiply result by 10 and add the digit.
   - Check for overflow before updating.
4. **Clamp result** to 32-bit integer boundaries if needed.
5. **Return** the final signed integer result.

---

## ✅ Java Code (Final Solution)

```java
class Solution {
    int myAtoi(String s) {
        if (s == null || s.length() == 0) return 0;

        int i = 0, n = s.length();
        int sign = 1;
        long result = 0;

        // 1. Skip leading whitespaces
        while (i < n && s.charAt(i) == ' ') {
            i++;
        }

        // 2. Handle optional sign
        if (i < n && (s.charAt(i) == '+' || s.charAt(i) == '-')) {
            sign = s.charAt(i) == '-' ? -1 : 1;
            i++;
        }

        // 3. Read digits and build number
        while (i < n && Character.isDigit(s.charAt(i))) {
            int digit = s.charAt(i) - '0';

            // 4. Check for overflow/underflow
            if (result > (Integer.MAX_VALUE - digit) / 10) {
                return sign == 1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            }

            result = result * 10 + digit;
            i++;
        }

        return (int) (sign * result);
    }
}
