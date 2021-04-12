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
