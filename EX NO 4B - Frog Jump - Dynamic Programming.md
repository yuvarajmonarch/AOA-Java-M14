
# EX 4B Frog Jump - Dynamic Programming.
## DATE: 11-11-2025
## AIM:
To write a Java program to for given constraints.
A Frog Jump 1 or 2 steps at a time.
Problem Statement:

A frog is at the bottom of the stairs with n steps. It can jump either 1 or 2 steps at a time. Write a program to find the number of distinct ways the frog can reach the top (n-th step).

Input Format:

A single integer n (1 ≤ n ≤ 45) – number of steps.
 Output Format:

A single integer – number of distinct ways to reach step n.

## Algorithm
1. Start  
2. Read the integer `n`, representing the number of stairs (or stones) the frog must jump.  
3. Define a function `countWays(n)` to calculate the total number of distinct ways the frog can reach the top:  
   - If `n == 1`, return `1` (only one way).  
   - If `n == 2`, return `2` (two ways: jump 1+1 or 2).  
4. Initialize two variables:  
   - `a = 1` → number of ways to reach step 1.  
   - `b = 2` → number of ways to reach step 2.  
5. For each step `i` from `3` to `n`:  
   - Compute `temp = a + b` → the number of ways to reach the current step is the sum of the previous two steps.  
   - Update `a = b` and `b = temp`.  
6. After the loop, `b` holds the total number of ways to reach step `n`.  
7. Print the result `b`.  
8. End  
   

## Program:
```
/*
Developed by: YUVARAJ B
Register Number:  212222040186
*/
import java.util.Scanner;

public class FrogJump {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        scanner.close();
        System.out.println(countWays(n));
    }

    public static int countWays(int n) {
        if (n == 1) return 1;
        if (n == 2) return 2;
        int a = 1, b = 2;
        for (int i = 3; i <= n; i++) {
            int temp = a + b;
            a = b;
            b = temp;
        }
        return b;
    }
}

```

## Output:

<img width="654" height="245" alt="image" src="https://github.com/user-attachments/assets/acc49917-2622-4899-bd15-56bf74bf95d9" />


## Result:
The program successfully implemented and the expected output is verified.
