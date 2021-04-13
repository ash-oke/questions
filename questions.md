# Questions discussed

1. Given a node 'p' of BST, and root, return the inorder successor of 'p'. Note that there is no pointer to parent.  
https://www.lintcode.com/problem/inorder-successor-in-bst/     
    <details>
        <summary>Quick Solution</summary>

    - If given node has right child, return the left most child of right child of 'p'.
    - Otherwise, starting from root, push all the parents till 'p' in stack and pop till immediate 
      parent is successor (`p.val < parent.val`)

    </details>

2. Given a list of pair of `<take_off, landing>` time of flights, return the maximum no of flights that will be in air simultaneously.  
https://www.lintcode.com/problem/number-of-airplanes-in-the-sky/
    <details>
        <summary>Quick Solution</summary>
    
    - Sort on `take_off` time
    - Push one by one in min_heap. min heap is constructed on landing time. 
    - If start time of incoming flight is greater than landing time of top of heap, pop heap until 
      start time of incoming flight is less that landing time of top of heap (or heap is empty).  
      Idea is to find overlapping flights.
    - Keep track of heap size after every insertion. Max of this would be the answer.

    </details>

3. Given a string array of 0's and 1's, find maximum subset of this array such that it has at most m 0's and n 1's.  
https://leetcode.com/problems/ones-and-zeroes/
    <details>
        <summary>Quick Solution</summary>
    
    - DP problem (0-1 knapsack variant).
    - For each element of array, try to follow two paths. Either take this and see if at most 
      conditions are met or ignore current element and try to fulfill conditions from other elements.

    </details>
    
4. Given an array of positive numbers and a positive target, find minimum contiguous subarray whose sum is greater  
   than or equal to `target`.  
https://leetcode.com/problems/minimum-size-subarray-sum/
    <details>
        <summary>Quick Solution</summary>
    
    - 2 pointer problem/sliding window problem.
    - Keep 2 pointers. The idea is that subarray defined by these 2 pointers would be the subarray which satisfies the
      given conditions.
    - Traverse each value from one end to another. Increase your ending pointer if the sum is still less than `target`.
    - If by adding the next element, the sum is greater than target, increase the starting pointer which denotes you are
      shrinking the array from beginning.
    - At each point in time, keep track what is the largest subarray size you saw.
    
    </details>

5. Given a array of integers, find the next permutation.  
https://leetcode.com/problems/next-permutation/
    <details>
        <summary>Quick Solution</summary>
    
    - Starting from last to first, find first entry which is non-increasing.
    - Find smallest greater element than the value found in step `1`. Again do this from the end.
    - Swap elements from step `1` and step `2`.
    - Reverse the subarray after index from step `1`.

    </details>
    
6. Given 2 strings, find the minimum no of deletions you need to make such that resulting strings are same.  
https://leetcode.com/problems/delete-operation-for-two-strings/

    <details>
        <summary>Quick Solution</summary>
    
    - Modified LCS.
    - Find the longest common subsequence in 2 strings using DP.
    - return `size1 + size2 - 2*(lcs)`
    
    </details>
    
7. Given a sorted array A of unique numbers, find the k-th missing number starting from the leftmost number of the array.  
https://leetcode.com/problems/missing-element-in-sorted-array/
https://code.dennyzhang.com/missing-element-in-sorted-array/
    <details>
        <summary>Quick Solution</summary>
        
    - Binary search
    - If the missing no falls in left half, search the missing no in left half. If it falls in right half,
      change the no of missing no to-be-searched by how many missing nos are gone in left half.
    - At any point of time, missing_nos_in_range = highest_value - lowest_value + 1 - range_size;

    </details>
    
8. Given n sorted lists, merge them and return single sorted merged list.  
https://leetcode.com/problems/merge-k-sorted-lists/
    <details>
        <summary>Quick Solution</summary>
        
    - One solution is to use min heap to keep track of minimum out of each head of list.
    - Keep incrementing head of lists which is added to final result list.
    - Second solution is to build on mergeSort which works on 2 lists.
    - If there are more than 2 lists, divide the no of lists in half and apply mergeSort. Do this step recursively.
    
    </details>
    
9. Given `n` and `k` such that `1 <= k < n`, return an array with values 1 to n such that the number of distinct
   differences between adjacent numbers is k.  
https://leetcode.com/problems/beautiful-arrangement-ii/
    <details>
        <summary>Quick Solution</summary>
    
    - If k = 1, return numbers in increasing order from 1 to n.
    - Keep 2 variables pointing to 1 and n, lets say i = 1, j = n.
    - while k != 1, alternatively push i/j to result array. Increment i if i is pushed/ decrement j if j is pushed.
      Reduce k.
    - Do step 1 when k reaches 1.

    </details>

10. Given an array `sum`, and 2 sums `sumA` and `sumB`, return 2 equal length arrays `A` and `B` consisting of only
    `0, 1` such that total sum of each array is equal to `sumA` and `sumB` respectively and `A[i]` + `B[i]` = `sum[i]`  
{TODO: Find out url of this question.}
    - Follow up: What if instead of filling up with just 0, 1, you could fill with numbers `1 to k`?

    <details>
        <summary>Quick Solution</summary>
        
    - At each index `i`, if `sum[i] == 2`, fill up `1` in both arrays `A` and `B`, and reduce `sumA` and `sumB` by 1.
    - If `sum[i] == 0`, fill up `0` in both arrays `A` and `B`.
    - if `sum[i] == 1`, fill up `1` in the array which has higher remaining sum.

    - TODO: Work out follow up question solution.
    
    </summary>
