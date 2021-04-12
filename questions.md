# Questions discussed

1. Given a node 'p' of BST, and root, return the inorder successor of 'p'. Note that there is no pointer to parent.  
https://leetcode.com/problems/inorder-successor-in-bst/     
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
    
    - Starting from last to first, find first entry which is
    - Find smallest greater element than the value found in step `1`.
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
