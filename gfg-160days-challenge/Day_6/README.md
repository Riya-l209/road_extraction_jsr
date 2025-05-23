# 💻 Day 6 - Majority Element II

**Difficulty:** Medium  
**Average Time:** 15 mins  
**Platform:** GeeksforGeeks  
**Points Earned:** 4 ✅

---

## 📘 Problem Statement:

You are given an array of integers `arr[]` where each number represents a vote to a candidate. Return the candidates that have votes **greater than one-third** of the total votes.  
If there's no such majority vote, return an empty array.

> 🔒 **Note:** The answer should be returned in **increasing order**.

---

## 🔍 Examples:

### Example 1:
Input: arr = [2, 1, 5, 5, 5, 6, 6, 6, 6, 6]
Output: [5, 6]
Explanation: 5 and 6 occur more than n/3 times.

shell
Copy
Edit

### Example 2:
Input: arr = [1, 2, 3, 4, 5]
Output: []
Explanation: No candidate occurs more than n/3 times.

---

## 📌 Constraints:

- 1 ≤ arr.length ≤ 10⁶  
- -10⁹ ≤ arr[i] ≤ 10⁹

---

## 🧠 Approach:

This is an extension of the **Boyer-Moore Majority Voting Algorithm**:
- Since we need elements appearing more than ⌊n/3⌋ times, there can be **at most two such elements**.
- Maintain two candidates and their counts.
- First loop: Identify potential candidates.
- Second loop: Validate their counts.
- Finally, return the valid candidates in **sorted order**.

---

## ⏱️ Time and Space Complexity:

- **Time Complexity:** O(n)  
- **Space Complexity:** O(1) (ignoring result list)

---

## 👨‍💻 Code (Java):

```java
class Solution {
    public List<Integer> findMajority(int[] nums) {
        int n = nums.length;
        int cand1 = 0, cand2 = 1;
        int count1 = 0, count2 = 0;

        for (int num : nums) {
            if (num == cand1) {
                count1++;
            } else if (num == cand2) {
                count2++;
            } else if (count1 == 0) {
                cand1 = num;
                count1 = 1;
            } else if (count2 == 0) {
                cand2 = num;
                count2 = 1;
            } else {
                count1--;
                count2--;
            }
        }

        count1 = 0;
        count2 = 0;
        for (int num : nums) {
            if (num == cand1) count1++;
            else if (num == cand2) count2++;
        }

        List<Integer> result = new ArrayList<>();
        if (count1 > n / 3) result.add(cand1);
        if (count2 > n / 3) result.add(cand2);
        Collections.sort(result);
        return result;
    }
}
✅ Output for Test Case:

Input:  [2, 1, 5, 5, 5, 6, 6, 6, 6, 6]  
Output: [5, 6]

📚 What I Learned:
Understood the modified Boyer-Moore Voting Algorithm.
Learned to identify up to two majority elements occurring more than n/3 times.
Improved understanding of space optimization for frequency-based problems.

