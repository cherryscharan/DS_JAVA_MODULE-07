# Ex9 Finding the Longest Length of Nested Set in a Permutation Array

## DATE: 18-09-2026

## AIM:

To write a Java program that finds the length of the longest set `s[k]` defined as:

`s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], ... }`

where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.

## Algorithm

1. Start and initialize the permutation array `nums` and set `maxLength = 0`.
2. For each index `k`, create a `visited` array and start from `nums[k]`.
3. Continue following `nums[current]` while the current element has not been visited.
4. Mark each visited element and count the number of elements in the current nested set.
5. Update `maxLength` if the current count is greater, then display the maximum length.

## Program:

```java
/*
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: charan kumar s
RegisterNumber:  212223220015
*/

import java.util.Scanner;

public class Main {

    static int findLongestSet(int[] nums) {

        int maxLength = 0;

        for (int k = 0; k < nums.length; k++) {

            boolean[] visited = new boolean[nums.length];

            int current = k;
            int count = 0;

            while (!visited[current]) {

                visited[current] = true;
                count++;

                current = nums[current];
            }

            if (count > maxLength) {
                maxLength = count;
            }
        }

        return maxLength;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        int result = findLongestSet(nums);

        System.out.println("Longest nested set length: " + result);
    }
}
```

## Output:

<img width="374" height="110" alt="image" src="https://github.com/user-attachments/assets/572ba65b-2c4d-4172-ada7-4fbea5060dae" />


## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
