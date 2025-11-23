
# EX 4C Coin Change Problem - Dynamic Programming.
## DATE: 11-11-2025
## AIM:
To write a Java program to for given constraints.
You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

## Algorithm
1. Start  
2. Read the list of coin denominations `coins[]` and the target `amount`.  
3. Initialize an array `dp[amount + 1]` to store the minimum number of coins needed for each value from `0` to `amount`.  
4. Fill the `dp` array with a large value (`amount + 1`) to represent infinity (unreachable state).  
5. Set `dp[0] = 0` (base case — zero coins are needed to make amount `0`).  
6. For each value `i` from `1` to `amount`:  
   - For each coin value `coin` in `coins`:  
     - If `i - coin >= 0`, update `dp[i] = min(dp[i], dp[i - coin] + 1)`  
       (choose the smaller count between existing value and using one more coin of the current denomination).  
7. After filling the table, check if `dp[amount] > amount`:  
   - If true → return `-1` (no combination of coins can make the target amount).  
   - Otherwise → return `dp[amount]` (minimum coins required).  
8. Print the result.  
9. End  


## Program:
```
/*
Developed by: YUVARAJ B
Register Number:  212222040186 
*/
import java.util.*;

public class Solution {
    public int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, amount + 1);
        dp[0] = 0;

        for (int i = 1; i <= amount; i++) {
            for (int coin : coins) {
                if (i - coin >= 0) {
                    dp[i] = Math.min(dp[i], dp[i - coin] + 1);
                }
            }
        }

        return dp[amount] > amount ? -1 : dp[amount];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution solution = new Solution();
        String coinsLine = scanner.nextLine(); 
        String amountLine = scanner.nextLine();

        coinsLine = coinsLine.replaceAll("[^0-9,]", ""); 
        String[] coinsStr = coinsLine.split(",");
        int[] coins = new int[coinsStr.length];
        for (int i = 0; i < coinsStr.length; i++) {
            coins[i] = Integer.parseInt(coinsStr[i]);
        }
        int amount = Integer.parseInt(amountLine.replaceAll("[^0-9]", ""));
        int result = solution.coinChange(coins, amount);
        System.out.println(result);

        scanner.close();
    }
}

```

## Output:

<img width="750" height="333" alt="image" src="https://github.com/user-attachments/assets/f067dd62-742f-4744-9222-b70a7cadfff2" />


## Result:
The program successfully implemented and the expected output is verified.
