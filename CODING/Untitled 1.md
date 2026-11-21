# DSA Placement Prep — Full Pattern Checklist

**Rule:** Don't check a topic off until you can solve a NEW problem in that pattern without seeing the approach first. Morning slot (7:30-8:40) = revise previous day's checked pattern from memory (re-derive, don't just re-read).

Legend: 🔑 Properties (what to actually understand) | 📝 Practice problems with LeetCode links (solve in order given) | ⭐ = highest-frequency / must-do if short on time

---
C:\Users\MyPc\Documents\Obsidian\Obsidian Vault
## 1. Arrays & Strings Basics

- [ ] **Prefix sum**
    
    - 🔑 Precompute cumulative sums so range-sum queries become O(1); prefix[i] = prefix[i-1] + arr[i]. Watch for prefix[-1]=0 edge case.
    - Practice:
        - ⭐[Range Sum Query - Immutable](https://leetcode.com/problems/range-sum-query-immutable/)
        - ⭐[Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)
        - [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)
        - [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) (combine with hashing)
- [ ] **Kadane's algorithm (max subarray)**
    
    - 🔑 At each index, decide: extend previous subarray or start fresh. O(n), O(1) space. Track global max separately from running max.
    - Practice:
        - ⭐[Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
        - ⭐[Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
        - [Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)
        - [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
- [ ] **Dutch National Flag (3-way partition)**
    
    - 🔑 Three pointers (low, mid, high) to partition array into 3 groups in one pass, O(n), O(1) space. Core idea behind quicksort's 3-way partitioning.
    - Practice:
        - ⭐[Sort Colors](https://leetcode.com/problems/sort-colors/)
        - ⭐Partition Array According to Given Pivot
        - 3-Way Quicksort practice
- [ ] **Cyclic sort (missing/duplicate number)**
    
    - 🔑 When array has numbers in range [1,n], place each number at its correct index (arr[i] = i+1) in O(n) without extra space.
    - Practice:
        - ⭐[Missing Number](https://leetcode.com/problems/missing-number/)
        - ⭐[Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)
        - [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)
        - [First Missing Positive](https://leetcode.com/problems/first-missing-positive/)

---

## 2. Two Pointers

- [ ] **Opposite-direction pointers**
    
    - 🔑 Start pointers at both ends, move inward based on comparison; works only on sorted data. O(n) instead of O(n²).
    - Practice:
        - ⭐[Two Sum II (sorted array)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
        - ⭐[3Sum](https://leetcode.com/problems/3sum/)
        - [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)
        - [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)
- [ ] **Fast-slow pointers**
    
    - 🔑 One pointer moves 2 steps, other 1 step — used to detect cycles or find the middle element without extra space.
    - Practice:
        - ⭐[Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)
        - ⭐[Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)
        - [Happy Number](https://leetcode.com/problems/happy-number/)
        - [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)
- [ ] **Merge two sorted arrays in-place**
    
    - 🔑 Fill from the back (largest elements first) to avoid overwriting unprocessed elements when one array has trailing empty space.
    - Practice:
        - ⭐[Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)
        - ⭐[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)
        - [Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)

---

## 3. Strings

- [ ] **Two pointers on string**
    
    - 🔑 Same as array two-pointers applied to characters; compare from both ends inward.
    - Practice:
        - ⭐[Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)
        - ⭐[Reverse String](https://leetcode.com/problems/reverse-string/)
        - [Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/)
        - [Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/)
- [ ] **Sliding window on string**
    
    - 🔑 Expand right pointer to grow window, shrink left pointer when condition breaks; track char counts in a hashmap.
    - Practice:
        - ⭐[Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
        - ⭐[Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
        - [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)
        - [Permutation in String](https://leetcode.com/problems/permutation-in-string/)
- [ ] **HashMap / frequency array**
    
    - 🔑 Character frequency count enables O(1) lookups for comparison problems; array of size 26 often beats hashmap for lowercase-only strings.
    - Practice:
        - ⭐[Valid Anagram](https://leetcode.com/problems/valid-anagram/)
        - ⭐[Group Anagrams](https://leetcode.com/problems/group-anagrams/)
        - [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)
        - [Ransom Note](https://leetcode.com/problems/ransom-note/)
- [ ] **String matching (KMP / Z-algorithm / Rabin-Karp)** _(skip unless targeting top-tier product companies)_
    
    - 🔑 KMP precomputes a "failure function" to avoid re-scanning matched characters; achieves O(n+m) vs brute force O(n·m).
    - Practice:
        - ⭐[Implement strStr()](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/)
        - ⭐Repeated String Match
        - [Shortest Palindrome](https://leetcode.com/problems/shortest-palindrome/)
- [ ] **Trie-based**
    
    - 🔑 Tree where each path from root represents a prefix; insert/search is O(L) where L = word length, independent of dictionary size.
    - Practice:
        - ⭐[Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)
        - ⭐[Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)
        - [Word Search II](https://leetcode.com/problems/word-search-ii/)
        - [Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/)
- [ ] **DP on strings** _(do after Dynamic Programming topic below)_
    
    - 🔑 Build a 2D table where dp[i][j] represents the answer for prefixes of length i and j of the two strings.
    - Practice:
        - ⭐[Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/)
        - ⭐[Edit Distance](https://leetcode.com/problems/edit-distance/)
        - [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)
        - [Longest Palindromic Subsequence](https://leetcode.com/problems/longest-palindromic-subsequence/)
- [ ] **Backtracking on string**
    
    - 🔑 Build the string character by character, branch on choices, undo (backtrack) when a branch fails or completes.
    - Practice:
        - ⭐[Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)
        - ⭐[Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)
        - [Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/)
        - Permutations of a String
- [ ] **Stack-based**
    
    - 🔑 LIFO order naturally matches nested/paired structures; push on open symbol, pop-and-check on close symbol.
    - Practice:
        - ⭐[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
        - ⭐[Decode String](https://leetcode.com/problems/decode-string/)
        - [Remove All Adjacent Duplicates in String](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/)
        - [Minimum Add to Make Parentheses Valid](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/)
- [ ] **Counting / math on string**
    
    - 🔑 Parse digit by digit, handle sign/overflow explicitly; simulate manual arithmetic for "multiply/add as strings."
    - Practice:
        - ⭐[String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/)
        - ⭐[Integer to Roman](https://leetcode.com/problems/integer-to-roman/)
        - [Multiply Strings](https://leetcode.com/problems/multiply-strings/)
        - [Add Binary](https://leetcode.com/problems/add-binary/)

---

## 4. Sliding Window (general, non-string)

- [ ] **Fixed-size window**
    
    - 🔑 Window size k is constant; slide by adding new element and removing the leftmost, updating running result in O(1) per step.
    - Practice:
        - ⭐[Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)
        - ⭐[Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)
        - [Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/)
- [ ] **Variable-size window**
    
    - 🔑 Window grows and shrinks based on a condition (sum, distinct count, etc.); each element added/removed at most once → O(n).
    - Practice:
        - ⭐[Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)
        - ⭐Longest Subarray of 1's After Deleting One Element
        - [Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)
- [ ] **Window + HashMap**
    
    - 🔑 Combine window boundaries with a frequency map to track "at most k distinct" type constraints.
    - Practice:
        - ⭐Longest Substring with At Most K Distinct Characters
        - ⭐[Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers/)

---

## 5. Hashing

- [ ] **Frequency map**
    
    - 🔑 O(1) average insert/lookup; trade space for time whenever you need "have I seen this before" checks.
    - Practice:
        - ⭐[Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)
        - ⭐[Majority Element](https://leetcode.com/problems/majority-element/)
        - [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
- [ ] **Two-sum pattern**
    
    - 🔑 Store (value → index) while iterating once; check complement existence before inserting current element.
    - Practice:
        - ⭐[Two Sum](https://leetcode.com/problems/two-sum/)
        - ⭐[4Sum II](https://leetcode.com/problems/4sum-ii/)
        - [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)
- [ ] **Group by key**
    
    - 🔑 Use a canonical form (sorted string, sorted tuple) as the hashmap key to cluster related elements.
    - Practice:
        - ⭐[Group Anagrams](https://leetcode.com/problems/group-anagrams/)
        - ⭐Group Shifted Strings
- [ ] **Prefix-sum + hashmap**
    
    - 🔑 Store prefix sums seen so far; if (currentPrefix - k) exists in map, a valid subarray ending here exists.
    - Practice:
        - ⭐[Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)
        - ⭐[Continuous Subarray Sum](https://leetcode.com/problems/continuous-subarray-sum/)
        - [Contiguous Array](https://leetcode.com/problems/contiguous-array/)

---

## 6. Recursion & Backtracking

- [ ] **Subsets / power set (include-exclude)**
    
    - 🔑 At each element, branch into two recursive calls: include it or exclude it. 2ⁿ total subsets.
    - Practice:
        - ⭐[Subsets](https://leetcode.com/problems/subsets/)
        - ⭐[Subsets II](https://leetcode.com/problems/subsets-ii/)
        - [Combination Sum](https://leetcode.com/problems/combination-sum/)
- [ ] **Permutations**
    
    - 🔑 Swap-based or visited-array based generation; track used elements to avoid repeats. n! total permutations.
    - Practice:
        - ⭐[Permutations](https://leetcode.com/problems/permutations/)
        - ⭐[Permutations II](https://leetcode.com/problems/permutations-ii/)
        - [Next Permutation](https://leetcode.com/problems/next-permutation/)
- [ ] **Combination sum**
    
    - 🔑 Backtrack while tracking remaining target; sort input first to prune early and skip duplicates cleanly.
    - Practice:
        - ⭐[Combination Sum](https://leetcode.com/problems/combination-sum/)
        - ⭐[Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)
        - [Combinations](https://leetcode.com/problems/combinations/)
- [ ] **N-Queens / Sudoku (constraint satisfaction)**
    
    - 🔑 Place one element per row/cell, check validity against existing placements before recursing, backtrack on failure.
    - Practice:
        - ⭐[N-Queens](https://leetcode.com/problems/n-queens/)
        - ⭐[Sudoku Solver](https://leetcode.com/problems/sudoku-solver/)
        - [Word Search](https://leetcode.com/problems/word-search/)

---

## 7. Binary Search

- [ ] **Standard BS on sorted array**
    
    - 🔑 Halve the search space each step by comparing mid element to target — O(log n). Watch integer overflow on mid calc.
    - Practice:
        - ⭐[Binary Search](https://leetcode.com/problems/binary-search/)
        - ⭐[Search Insert Position](https://leetcode.com/problems/search-insert-position/)
- [ ] **BS on answer (search space reduction)**
    
    - 🔑 Binary search over the range of possible _answers_ (not array indices); needs a monotonic "is this answer feasible?" check.
    - Practice:
        - ⭐[Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/)
        - ⭐[Capacity To Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)
        - [Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/)
- [ ] **BS on rotated array**
    
    - 🔑 One half of the array around mid is always sorted; determine which half and check if target lies in that range.
    - Practice:
        - ⭐[Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
        - ⭐[Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
        - [Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)
- [ ] **First/last occurrence**
    
    - 🔑 Modify standard BS to keep searching left (or right) even after finding a match, to find the boundary.
    - Practice:
        - ⭐[Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
        - ⭐Count Occurrences in Sorted Array

---

## 8. Sorting

- [ ] **Merge sort (inversion count)**
    
    - 🔑 Divide-and-conquer, O(n log n); count cross-inversions during the merge step when left[i] > right[j].
    - Practice:
        - ⭐[Sort an Array](https://leetcode.com/problems/sort-an-array/)
        - ⭐[Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/)
        - [Reverse Pairs](https://leetcode.com/problems/reverse-pairs/)
- [ ] **Quickselect (kth largest/smallest)**
    
    - 🔑 Like quicksort but recurse into only one partition; average O(n), worst O(n²).
    - Practice:
        - ⭐[Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)
        - ⭐[Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
        - [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)
- [ ] **Interval merging/overlap**
    
    - 🔑 Sort by start time first; merge current interval into previous if it overlaps (current.start ≤ previous.end).
    - Practice:
        - ⭐[Merge Intervals](https://leetcode.com/problems/merge-intervals/)
        - ⭐[Insert Interval](https://leetcode.com/problems/insert-interval/)
        - [Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)
        - [Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/)

---

## 9. Linked List

- [ ] **Fast-slow pointer (cycle, middle)**
    
    - 🔑 Floyd's Tortoise and Hare: fast catches slow inside a cycle; slow lands on middle when fast reaches the end.
    - Practice:
        - ⭐[Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)
        - ⭐[Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)
        - [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)
- [ ] **Reverse (iterative / in groups)**
    
    - 🔑 Track prev, curr, next pointers; reverse the `next` link one node at a time. For groups, reverse in chunks of k.
    - Practice:
        - ⭐[Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
        - ⭐[Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/)
        - [Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)
- [ ] **Dummy node technique**
    
    - 🔑 A placeholder node before head simplifies edge cases (empty list, removing head) — avoids null-checks scattered everywhere.
    - Practice:
        - ⭐[Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)
        - ⭐[Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)
        - [Partition List](https://leetcode.com/problems/partition-list/)
- [ ] **Merge two lists**
    
    - 🔑 Compare heads of both lists, attach the smaller to result, advance that pointer — same idea as merge step of merge sort.
    - Practice:
        - ⭐[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)
        - ⭐[Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)
        - [Sort List](https://leetcode.com/problems/sort-list/)

---

## 10. Stack & Queue

- [ ] **Monotonic stack**
    
    - 🔑 Maintain stack in increasing/decreasing order; pop elements that violate order before pushing — gives O(n) "next greater/smaller."
    - Practice:
        - ⭐[Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)
        - ⭐[Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)
        - [Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)
        - [Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)
- [ ] **Valid parentheses (matching)**
    
    - 🔑 Push opening brackets, pop and match on closing brackets; stack empty at end = valid.
    - Practice:
        - ⭐[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
        - ⭐[Remove Invalid Parentheses](https://leetcode.com/problems/remove-invalid-parentheses/)
        - [Score of Parentheses](https://leetcode.com/problems/score-of-parentheses/)
- [ ] **Min stack (auxiliary stack)**
    
    - 🔑 Maintain a second stack tracking the minimum-so-far alongside the main stack for O(1) getMin().
    - Practice:
        - ⭐[Min Stack](https://leetcode.com/problems/min-stack/)
        - ⭐[Max Stack](https://leetcode.com/problems/max-stack/)
        - [Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)

---

## 11. Trees (Binary Tree / BST)

- [ ] **DFS (pre/in/post) recursive & iterative**
    
    - 🔑 Recursive uses call stack implicitly; iterative uses explicit stack. In-order on BST gives sorted sequence.
    - Practice:
        - ⭐Binary Tree Inorder/Preorder/Postorder Traversal
        - ⭐[Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)
- [ ] **BFS (level order)**
    
    - 🔑 Use a queue; process one level fully before moving to next — track level size to separate levels.
    - Practice:
        - ⭐[Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
        - ⭐[Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)
        - [Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)
- [ ] **Height/diameter via post-order**
    
    - 🔑 Compute children's heights first (post-order), combine at parent; diameter = max(left height + right height) across all nodes.
    - Practice:
        - ⭐[Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
        - ⭐[Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)
        - [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)
- [ ] **BST property traversal**
    
    - 🔑 Left < Node < Right holds for every node; in-order traversal of a valid BST is always sorted.
    - Practice:
        - ⭐[Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)
        - ⭐[Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)
        - [Convert Sorted Array to BST](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)
- [ ] **LCA (lowest common ancestor)**
    
    - 🔑 Recurse into both subtrees; if a node is found in both, it's the LCA. For BST, use value comparison to go left/right.
    - Practice:
        - ⭐[Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)
        - ⭐[Lowest Common Ancestor of a BST](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

---

## 12. Heap / Priority Queue

- [ ] **Top-K elements (min-heap of size k)**
    
    - 🔑 Maintain a heap of size k; if new element is larger than heap top (for "top k largest"), pop and push. O(n log k).
    - Practice:
        - ⭐[Kth Largest Element in a Stream](https://leetcode.com/problems/kth-largest-element-in-a-stream/)
        - ⭐[Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
        - [K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)
- [ ] **Two heaps (median in stream)**
    
    - 🔑 Max-heap for lower half, min-heap for upper half; keep sizes balanced (differ by ≤1) for O(1) median access.
    - Practice:
        - ⭐[Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)
        - ⭐[Sliding Window Median](https://leetcode.com/problems/sliding-window-median/)
- [ ] **Merge k sorted lists**
    
    - 🔑 Push first element of each list into a min-heap; pop min, push its successor — O(n log k).
    - Practice:
        - ⭐[Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)
        - ⭐[Smallest Range Covering Elements from K Lists](https://leetcode.com/problems/smallest-range-covering-elements-from-k-lists/)

---

## 13. Graphs

- [ ] **BFS/DFS traversal (connected components)**
    
    - 🔑 Visited-set prevents revisiting; each unvisited node you start from = one new component.
    - Practice:
        - ⭐[Number of Islands](https://leetcode.com/problems/number-of-islands/)
        - ⭐[Number of Provinces](https://leetcode.com/problems/number-of-provinces/)
        - [Flood Fill](https://leetcode.com/problems/flood-fill/)
- [ ] **Topological sort (Kahn's / DFS)**
    
    - 🔑 Only valid on DAGs; Kahn's uses in-degree counting + queue, DFS-based uses post-order reversal.
    - Practice:
        - ⭐[Course Schedule](https://leetcode.com/problems/course-schedule/)
        - ⭐[Course Schedule II](https://leetcode.com/problems/course-schedule-ii/)
        - [Alien Dictionary](https://leetcode.com/problems/alien-dictionary/)
- [ ] **Union-Find (Disjoint Set)**
    
    - 🔑 Union by rank + path compression gives near-O(1) amortized operations; detects cycles in undirected graphs.
    - Practice:
        - ⭐[Number of Provinces](https://leetcode.com/problems/number-of-provinces/)
        - ⭐[Redundant Connection](https://leetcode.com/problems/redundant-connection/)
        - [Accounts Merge](https://leetcode.com/problems/accounts-merge/)
- [ ] **Dijkstra (shortest path, weighted)**
    
    - 🔑 Greedy + min-heap; always expand the currently-closest unvisited node. Doesn't work with negative weights.
    - Practice:
        - ⭐[Network Delay Time](https://leetcode.com/problems/network-delay-time/)
        - ⭐[Cheapest Flights Within K Stops](https://leetcode.com/problems/cheapest-flights-within-k-stops/)
        - [Path with Maximum Probability](https://leetcode.com/problems/path-with-maximum-probability/)

---

## 14. Dynamic Programming

- [ ] **0/1 Knapsack**
    
    - 🔑 Each item used at most once; dp[i][w] = max value using first i items with capacity w. Iterate weight in reverse for space-optimized version.
    - Practice:
        - ⭐[Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/)
        - ⭐[Target Sum](https://leetcode.com/problems/target-sum/)
        - [Last Stone Weight II](https://leetcode.com/problems/last-stone-weight-ii/)
- [ ] **Unbounded Knapsack**
    
    - 🔑 Items can be reused unlimited times; iterate weight forward (not reverse) since reuse is allowed.
    - Practice:
        - ⭐[Coin Change](https://leetcode.com/problems/coin-change/)
        - ⭐[Coin Change II](https://leetcode.com/problems/coin-change-ii/)
        - [Combination Sum IV](https://leetcode.com/problems/combination-sum-iv/)
- [ ] **LCS family**
    
    - 🔑 dp[i][j] built from dp[i-1][j-1] (match) or max(dp[i-1][j], dp[i][j-1]) (no match).
    - Practice:
        - ⭐[Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/)
        - ⭐[Delete Operation for Two Strings](https://leetcode.com/problems/delete-operation-for-two-strings/)
        - [Shortest Common Supersequence](https://leetcode.com/problems/shortest-common-supersequence/)
- [ ] **LIS (Longest Increasing Subsequence)**
    
    - 🔑 O(n²) DP or O(n log n) with binary search + patience sorting idea.
    - Practice:
        - ⭐[Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)
        - ⭐[Russian Doll Envelopes](https://leetcode.com/problems/russian-doll-envelopes/)
        - [Maximum Length of Pair Chain](https://leetcode.com/problems/maximum-length-of-pair-chain/)
- [ ] **DP on grid**
    
    - 🔑 dp[i][j] depends on dp[i-1][j] and dp[i][j-1] — movement only right/down; base case is first row/column.
    - Practice:
        - ⭐[Unique Paths](https://leetcode.com/problems/unique-paths/)
        - ⭐[Unique Paths II](https://leetcode.com/problems/unique-paths-ii/)
        - [Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/)
        - [Dungeon Game](https://leetcode.com/problems/dungeon-game/)
- [ ] **DP on strings (edit distance, palindrome)**
    
    - 🔑 dp[i][j] = min operations to convert prefix i of s1 to prefix j of s2; three choices — insert, delete, replace.
    - Practice:
        - ⭐[Edit Distance](https://leetcode.com/problems/edit-distance/)
        - ⭐[Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)
        - [Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/)

---

## 15. Greedy

- [ ] **Activity selection / interval scheduling**
    
    - 🔑 Sort by end time, always pick the interval that finishes earliest and is compatible — provably optimal.
    - Practice:
        - ⭐[Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)
        - ⭐[Meeting Rooms](https://leetcode.com/problems/meeting-rooms/)
        - [Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)
- [ ] **Jump game (reachability)**
    
    - 🔑 Track the farthest index reachable so far; greedy works because farther reach never hurts.
    - Practice:
        - ⭐[Jump Game](https://leetcode.com/problems/jump-game/)
        - ⭐[Jump Game II](https://leetcode.com/problems/jump-game-ii/)
        - [Gas Station](https://leetcode.com/problems/gas-station/)
- [ ] **Fractional knapsack**
    
    - 🔑 Sort by value/weight ratio, take highest-ratio items first (fully or fractionally) — greedy is optimal here (unlike 0/1 knapsack).
    - Practice:
        - ⭐Fractional Knapsack (GfG/interview-style)
        - ⭐[Maximum Units on a Truck](https://leetcode.com/problems/maximum-units-on-a-truck/)

---

## 16. Bit Manipulation

- [ ] **XOR trick (single number)**
    
    - 🔑 a XOR a = 0, a XOR 0 = a; XOR of all elements cancels out pairs, leaves the unique one.
    - Practice:
        - ⭐[Single Number](https://leetcode.com/problems/single-number/)
        - ⭐[Single Number II](https://leetcode.com/problems/single-number-ii/)
        - [Single Number III](https://leetcode.com/problems/single-number-iii/)
- [ ] **Bit masking for subsets**
    
    - 🔑 Represent each subset as an n-bit integer (0 to 2ⁿ-1); bit i set = element i included.
    - Practice:
        - ⭐Subsets (bitmask approach)
        - ⭐[Sum of All Subset XOR Totals](https://leetcode.com/problems/sum-of-all-subset-xor-totals/)
- [ ] **Count set bits**
    
    - 🔑 Brian Kernighan's trick: n & (n-1) clears the lowest set bit — loop runs once per set bit, not per bit position.
    - Practice:
        - ⭐[Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)
        - ⭐[Counting Bits](https://leetcode.com/problems/counting-bits/)
        - [Reverse Bits](https://leetcode.com/problems/reverse-bits/)

---

## 17. Trie

- [ ] **Insert/search/prefix match**
    
    - 🔑 Each node holds a map/array of children (one per possible character) and an end-of-word flag.
    - Practice:
        - ⭐[Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)
        - ⭐[Longest Word in Dictionary](https://leetcode.com/problems/longest-word-in-dictionary/)
        - [Map Sum Pairs](https://leetcode.com/problems/map-sum-pairs/)
- [ ] **Word search with backtracking + trie**
    
    - 🔑 Combine grid DFS backtracking with a trie to prune paths early when no dictionary word matches the prefix so far.
    - Practice:
        - ⭐[Word Search II](https://leetcode.com/problems/word-search-ii/)
        - ⭐[Word Break II](https://leetcode.com/problems/word-break-ii/)

---

### Second pass (do after finishing all topics once)

- [ ] Re-solve one random problem per topic (mixed order, no topic hint) — simulates real interview conditions

---

**Note on LeetCode links:** every problem above is linked directly except **"Partition Array According to Given Pivot"**, **"3-Way Quicksort practice"**, and **"Fractional Knapsack"** — these three are GeeksforGeeks-style problems not available on LeetCode in that exact form; search them on GfG instead.