
# EX 4A Kadane's Algorithm - Dynamic Programming. 
## DATE: 11-11-2025
## AIM:
To Write a Java program to solve the below problem using Kadane's Algorithm.
A solar company installs solar panels around a circular grid of n buildings. Each building either generates or consumes net energy, represented by integers (+ve for generated, -ve for consumed).

The company wants to find a contiguous sequence of buildings (possibly wrapping around from the end to the beginning) that maximizes the total net energy.

Write a program to compute the maximum net energy that can be collected from any contiguous block of buildings on the circular grid.

Input Format:
First line: Integer n (number of buildings)

Second line: n space-separated integers: net energy for each building

Output Format:
A single integer: Maximum net energy collectable from a contiguous block (wrapping allowed)

Constraints:
1 <= n <= 10^6
## Algorithm
1. Start  
2. Read the integer `n` (number of solar panels or energy readings).  
3. Input `n` energy values into the array `energy[]`.  
4. Define a helper function `kadane(arr)` to find the maximum subarray sum in a normal (non-circular) array:  
   - Initialize `maxEndingHere = arr[0]` and `maxSoFar = arr[0]`.  
   - For each element from index `1` to `n-1`:  
     - Update `maxEndingHere = max(arr[i], maxEndingHere + arr[i])`.  
     - Update `maxSoFar = max(maxSoFar, maxEndingHere)`.  
   - Return `maxSoFar`.  
5. In the main logic (`maxCircularEnergy`):  
   - Compute `maxKadane = kadane(energy)` — the maximum subarray sum without wrapping.  
   - Calculate the total sum of all elements: `totalSum = sum(energy)`.  
   - Create an inverted array `inverted[i] = -energy[i]` for all `i`.  
   - Compute `maxWrap = totalSum + kadane(inverted)` — the maximum sum of a circular subarray (using the formula for wraparound sum).  
6. If `maxWrap == 0`, it means all numbers are negative → return `maxKadane`.  
7. Otherwise, return the maximum of `maxKadane` and `maxWrap`.  
8. Print the result — the maximum possible solar energy capture in circular arrangement.  
9. End  
   

## Program:
```
/*
Developed by: YUVARAJ B
Register Number:  212222040186 
*/
import java.util.*;

public class SolarEnergyMaximizer {

    private static int kadane(int[] arr) {
        int maxEndingHere = arr[0];
        int maxSoFar = arr[0];
        for (int i = 1; i < arr.length; i++) {
            maxEndingHere = Math.max(arr[i], maxEndingHere + arr[i]);
            maxSoFar = Math.max(maxSoFar, maxEndingHere);
        }
        return maxSoFar;
    }

    public static int maxCircularEnergy(int[] energy) {
        int n = energy.length;
        int maxKadane = kadane(energy);
        int totalSum = 0;
        int[] inverted = new int[n];
        for (int i = 0; i < n; i++) {
            totalSum += energy[i];
            inverted[i] = -energy[i];
        }
        int maxWrap = totalSum + kadane(inverted);
        return maxWrap == 0 ? maxKadane : Math.max(maxKadane, maxWrap);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] energy = new int[n];
        for (int i = 0; i < n; i++) {
            energy[i] = sc.nextInt();
        }
        System.out.println(maxCircularEnergy(energy));
        sc.close();
    }
}

```

## Output:

<img width="825" height="382" alt="image" src="https://github.com/user-attachments/assets/30e9c409-4cfe-463c-8822-bef3d2a15502" />


## Result:
The program successfully Implemented and the output is verified. 
