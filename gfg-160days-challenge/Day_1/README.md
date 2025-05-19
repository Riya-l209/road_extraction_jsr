# Day 1 - Second Largest in Array

### Problem:
[Second Largest - GeeksforGeeks](https://www.geeksforgeeks.org/problems/second-largest3735/1)

*Task:* Given an array of positive integers, return the second largest element. If it doesn't exist, return -1.

### Example:
- Input: [12, 35, 1, 10, 34, 1] → Output: 34
- Input: [10, 10, 10] → Output: -1

---

### Code (Java):
```java
class Solution {
    public static int getSecondLargest(int[] arr) {
        if (arr == null || arr.length < 2) return -1;

        int largest = Integer.MIN_VALUE;
        int getSecondLargest = Integer.MIN_VALUE;

        for (int num : arr) {
            if (num > largest) {
                getSecondLargest = largest;
                largest = num;
            } else if (num > getSecondLargest && num != largest) {
                getSecondLargest = num;
            }
        }

        return (getSecondLargest == Integer.MIN_VALUE) ? -1 : getSecondLargest;
    }

    public static void main(String[] args) {
        int[] arr1 = {12, 35, 1, 10, 34, 1};
        int[] arr2 = {10, 5, 10};
        int[] arr3 = {10, 10, 10};

        System.out.println(getSecondLargest(arr1));
        System.out.println(getSecondLargest(arr2));
        System.out.println(getSecondLargest(arr3));
    }
}