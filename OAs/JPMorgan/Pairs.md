# 1. Pairs
[See Problem on HackerRank](https://www.hackerrank.com)

## Problem Description

You are given two arrays `a[n]` and `b[n]`. The task is to find the maximum number of pairs that can be formed where `a[i] > b[j]`. Each element can only be part of one pair. Return the maximum number of such pairs.

### Example 1:
Input:  
```  
a = [1, 2, 3]  
b = [1, 2, 1]  
```
Output:  
```
2  
```
Explanation: The valid pairs are:
- Pair `a[1] = 2` with `b[2] = 1`
- Pair `a[2] = 3` with `b[1] = 1`
Thus, the maximum number of pairs is 2.

### Example 2:
Input:  
```  
a = [1, 2, 3, 4, 5]  
b = [6, 6, 1, 1, 1]  
```
Output:  
```
3  
```
Explanation:  
The valid pairs are:
- Pair `a[4] = 5` with `b[2] = 1`
- Pair `a[3] = 4` with `b[3] = 1`
- Pair `a[2] = 3` with `b[4] = 1`

### Constraints:
- \(1 \leq n \leq 10^5\)
- \(1 \leq a[i], b[i] \leq 10^9\)

## My Solution
> **Difficulty Level:** Medium | **Language:** Java

```java
import java.util.*;

class Result {

    public static int findNumOfPairs(List<Integer> a, List<Integer> b) {
        // Sort both arrays
        Collections.sort(a);
        Collections.sort(b);

        int numOfPairs = 0;
        int i = a.size() - 1; // Pointer for array a
        int j = b.size() - 1; // Pointer for array b

        // Traverse both arrays using two pointers from the largest elements
        while (i >= 0 && j >= 0) {
            if (a.get(i) > b.get(j)) {
                numOfPairs++;  // Form a valid pair
                i--;  // Move both pointers to find the next largest pair
                j--;
            } else {
                j--;  // If no pair is possible, move pointer in b to the next largest
            }
        }
        return numOfPairs;
    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int aCount = Integer.parseInt(bufferedReader.readLine().trim());

        List<Integer> a = new ArrayList<>();
        for (int i = 0; i < aCount; i++) {
            a.add(Integer.parseInt(bufferedReader.readLine().trim()));
        }

        int bCount = Integer.parseInt(bufferedReader.readLine().trim());

        List<Integer> b = new ArrayList<>();
        for (int i = 0; i < bCount; i++) {
            b.add(Integer.parseInt(bufferedReader.readLine().trim()));
        }

        int result = Result.findNumOfPairs(a, b);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}
```

**Runtime:** `O(n log n)` (for sorting the arrays)  
**Memory:** Efficient  
**Time Complexity:** `O(n log n)`  
**Space Complexity:** `O(n)`

### How I approached it:
#### Intuition:
1. **Sorting for Optimal Pairing**: By sorting both arrays, we can efficiently match the largest possible elements from `a[]` with the largest elements from `b[]` that satisfy the condition `a[i] > b[j]`.
2. **Two-Pointer Technique**: After sorting both arrays, we use two pointers starting from the largest elements of each array to find the maximum number of valid pairs.

#### Algorithm Explanation:
1. **Step 1**: Sort both arrays in ascending order.
2. **Step 2**: Initialize two pointers at the end of both arrays (the largest elements).
3. **Step 3**: Check if `a[i] > b[j]`. If true, form a pair and decrement both pointers.
4. **Step 4**: If `a[i] <= b[j]`, just decrement the pointer for array `b` to try the next largest element.
5. **Final Step**: Continue this process until one of the arrays is fully traversed. The count of valid pairs will be stored in `numOfPairs`.

#### Complexity Analysis:
- **Time Complexity**: `O(n log n)` because we need to sort both arrays before applying the two-pointer technique.
- **Space Complexity**: `O(n)` to store the input arrays and intermediate data during sorting.

#### Performance:
- **Runtime**: Efficient for large inputs due to sorting and the two-pointer approach.
- **Memory Usage**: Moderate, proportional to the input size.
