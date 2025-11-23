
# EX 4D Longest Common SubSequence - Dynamic Programming.
## DATE: 11-11-2025
## AIM:
To write a Java program to for given constraints.
Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.
A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".
A common subsequence of two strings is a subsequence that is common to both strings.

Input: text1 = "abcde", text2 = "ace" 
Output: 3  
Explanation: The longest common subsequence is "ace" and its length is 3.
Constraints:

1 <= text1.length, text2.length <= 1000
text1 and text2 consist of only lowercase English characters.

## Algorithm
1. Start  
2. Read two input strings `text1` and `text2`.  
3. Let `m = length of text1` and `n = length of text2`.  
4. Create a 2D array `dp[m + 1][n + 1]`, where `dp[i][j]` represents the length of the LCS of the first `i` characters of `text1` and the first `j` characters of `text2`.  
5. Initialize the first row and first column of `dp` to `0` (base case — when one string is empty, the LCS length is `0`).  
6. Fill the DP table using the following logic:  
   - For each `i` from `1` to `m`:  
     - For each `j` from `1` to `n`:  
       - If `text1[i - 1] == text2[j - 1]`, then  
         `dp[i][j] = 1 + dp[i - 1][j - 1]`  
         (characters match — include it in the LCS).  
       - Else,  
         `dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])`  
         (characters don’t match — take the longer LCS found so far).  
7. After filling the table, the value `dp[m][n]` gives the **length of the longest common subsequence**.  
8. Print `dp[m][n]`.  
9. End  
 

## Program:
```
/*
Developed by: YUVARAJ B
Register Number:  212222040186
*/

import java.util.Scanner;

public class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();

        int[][] dp = new int[m + 1][n + 1];

        // Build the dp table
        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                    dp[i][j] = 1 + dp[i - 1][j - 1];
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }

        return dp[m][n];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        String text1 = sc.nextLine().replaceAll("\"", "");
        String text2 = sc.nextLine().replaceAll("\"", "");

        int lcsLength = sol.longestCommonSubsequence(text1, text2);
        System.out.println("Length of Longest Common Subsequence: " + lcsLength);

        sc.close();
    }
}

```

## Output:

<img width="1018" height="334" alt="image" src="https://github.com/user-attachments/assets/fe467514-499b-41f4-9f13-1cd74c3fbbec" />


## Result:
The program successfully implemented and the expected output is verified.
