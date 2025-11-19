# Ex9 Finding the Longest Length of Nested Set in a Permutation Array
## DATE:
## AIM:
To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.
## Algorithm
```text
1. Start
2. Read the integer n
3. Read n integers into the array nums[0..n-1]
4. Create a boolean array visited[0..n-1] and set all entries to false
5. Set maxLen = 0
6. For i from 0 to n - 1, do:
   a) If visited[i] is false, then:
       i) Set count = 0
      ii) Set current = i
     iii) While visited[current] is false:
             - Set visited[current] = true
             - Set current = nums[current]
             - Increment count by 1
      iv) If count > maxLen, set maxLen = count
7. After the loop ends, maxLen holds the length of the largest set s[k]
8. Print maxLen
9. End

```

## Program:
Program to find the Longest Length of Nested Set in a Permutation Array
```java
import java.util.Scanner;

public class Main {
    static int arrayNesting(int[] nums) {
        int n = nums.length;
        boolean[] visited = new boolean[n];
        int maxLen = 0;
        for (int i = 0; i < n; i++) {
            if (!visited[i]) {
                int count = 0;
                int current = i;
                while (!visited[current]) {
                    visited[current] = true;
                    current = nums[current];
                    count++;
                }
                if (count > maxLen)
                    maxLen = count;
            }
        }
        return maxLen;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++)
            nums[i] = sc.nextInt();
        System.out.println(arrayNesting(nums));
        sc.close();
    }
}

```
Developed by: THILAK RAJ . P  
RegisterNumber:  212224040353

## Output:

<img width="376" height="241" alt="image" src="https://github.com/user-attachments/assets/f08dbf21-17a8-48d1-b657-3c0b76e8d3ab" />


## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
