# Second Largest Element in Array

**Difficulty:** Easy  
**Accuracy:** 26.72%  
**Average Time:** 15 min  

---

## Problem Statement
Given an array of positive integers `arr[]`, return the **second largest** element from the array.  
If the second largest element doesn't exist, return `-1`.

> **Note:** The second largest element should not be equal to the largest element.

---

## Examples

### Example 1
**Input:**  
arr[] = [12, 35, 1, 10, 34, 1]

makefile
Copy
Edit
**Output:**  
34

yaml
Copy
Edit
**Explanation:**  
The largest element is `35`, and the second largest is `34`.

---

### Example 2
**Input:**  
arr[] = [10, 5, 10]

makefile
Copy
Edit
**Output:**  
5

markdown
Copy
Edit
**Explanation:**  
The largest element is `10`, and the second largest is `5`.

---

## Approach

We can solve this in **one pass** through the array:

1. Initialize two variables:
   - `firstLarg` → stores the largest element found so far.
   - `secondLarg` → stores the second largest element found so far.
   Both are initialized to `-1` (since array contains **positive integers**).

2. Traverse the array:
   - If the current element is **greater than** `firstLarg`:
     - Update `secondLarg` to `firstLarg`.
     - Update `firstLarg` to the current element.
   - Else if the current element is **less than** `firstLarg` **and greater than** `secondLarg`:
     - Update `secondLarg` to the current element.

3. Return `secondLarg`.

---

## Code Implementation (Java)

```java
class Solution {
    public int getSecondLargest(int[] arr) {
        int firstLarg = -1, secondLarg = -1;
        int n = arr.length;

        for (int i = 0; i < n; i++) {
            if (arr[i] > firstLarg) {
                // Found new largest, update second largest before changing first largest
                secondLarg = firstLarg;
                firstLarg = arr[i];
            }
            else if (arr[i] < firstLarg && arr[i] > secondLarg) {
                // Found a number between first and second largest
                secondLarg = arr[i];
            }
        }
        return secondLarg;
    }
}
Time Complexity
O(n) → We traverse the array once.

Space Complexity
O(1) → No extra space used except for a few variables.

Key Points
Handles duplicate largest elements (second largest must be strictly smaller than largest).

Works in a single pass, making it efficient.

Returns -1 if no second largest element exists.
