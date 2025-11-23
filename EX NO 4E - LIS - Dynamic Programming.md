
# EX 4E Longest Increasing Subsequence - Dynamic Programming.
## DATE: 11-11-2025
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return the length of the longest strictly increasing subsequence.
Example 1:
Input: nums = [10,9,2,5,3,7,101,18]
Output: 4
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
## Algorithm
1. Start  
2. Read the integer `n` (number of elements in the array).  
3. Input `n` integers into the array `nums[]`.  
4. Initialize an array `dp[n]`, where `dp[i]` represents the length of the **Longest Increasing Subsequence (LIS)** ending at index `i`.  
5. Set all values in `dp` to `1` (each element is an LIS of length `1` by itself).  
6. Initialize a variable `maxLen = 1` to track the overall longest LIS length.  
7. For each element `i` from `1` to `n-1`:  
   - For each previous element `j` from `0` to `i-1`:  
     - If `nums[i] > nums[j]`, then update `dp[i] = max(dp[i], dp[j] + 1)`.  
       (This means the subsequence ending at `j` can be extended by `nums[i]`.)  
   - Update `maxLen = max(maxLen, dp[i])`.  
8. After the loops, `maxLen` contains the length of the longest increasing subsequence.  
9. Print `maxLen`.  
10. End  
 

## Program:
```
/*
Developed by: YUVARAJ B
Register Number:  212222040186  
*/

import java.util.*;
public class LongestIncreasingSubsequence {

    public static int lengthOfLIS(int[] nums) {
        int n = nums.length;
        int[] dp = new int[n];
        Arrays.fill(dp, 1); // Each element is an LIS of length 1 by itself

        int maxLen = 1;

        // Build up dp table
        for (int i = 1; i < n; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
            maxLen = Math.max(maxLen, dp[i]);
        }

        return maxLen;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }

        int result = lengthOfLIS(nums);
        System.out.println("Length of Longest Increasing Subsequence: " + result);

        scanner.close();
    }
}

```

## Output:

<img width="1222" height="358" alt="image" src="https://github.com/user-attachments/assets/a305eb9c-dd9e-4569-9375-5cf9be1c5543" />


## Result:
The program successfully implemented and the expected output is verified.
