🧠 Non Repeating Character
Problem Link: GeeksforGeeks - Non Repeating Character

📝 Problem Statement
Given a string s consisting of lowercase English letters, return the first non-repeating character in s.
If there is no non-repeating character, return $.
Note: When you return $, the driver code will output -1.

🧾 Examples

Input: s = "geeksforgeeks"
Output: f
Explanation: 'f' is the first character in the string which does not repeat.

Input: s = "racecar"
Output: e
Explanation: 'e' is the only character that does not repeat.

Input: s = "aabbccc"
Output: -1
Explanation: All characters in the string are repeating.
🎯 Constraints
1 ≤ |s| ≤ 100
s contains only lowercase English letters.

💡 Approach
We will solve the problem using frequency counting:
Count the frequency of each character using an integer array of size 26 (for all lowercase alphabets).
Traverse the string again and return the first character that has frequency 1.
If none found, return '$', which will be printed as -1 by the driver.

🔄 Steps Involved
Initialize an integer array freq[26] to 0.
Traverse the input string and increase the count for each character in the frequency array.
Traverse the string again, and for each character, check if its frequency is 1.
Return the first such character.
If none found, return $.

📌 Java Code
java
class Solution {
    static char nonRepeatingChar(String s) {
        int[] freq = new int[26];

        // Count frequency of each character
        for (int i = 0; i < s.length(); i++) {
            freq[s.charAt(i) - 'a']++;
        }

        // Find first non-repeating character
        for (int i = 0; i < s.length(); i++) {
            if (freq[s.charAt(i) - 'a'] == 1) {
                return s.charAt(i);
            }
        }

        return '$';
    }
}

✅ Input Format
A single string s containing only lowercase English letters.

🧾 Output Format
The first non-repeating character in the string.

If none exists, return $ (displayed as -1).

🧠 Time & Space Complexity
Time Complexity: O(n) where n is the length of the string (due to two traversals).
Space Complexity: O(1) since the size of frequency array is constant (26).

