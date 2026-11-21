### STRINGS

- [x]  Reverse a String
- [ ]  Check Palindrome String
- [ ]  Count Vowels
- [ ]  Count Consonants
- [ ]  Remove Duplicate Characters
- [ ]  Find Duplicate Characters
- [ ]  Check Anagram
- [ ]  Count Words
- [ ]  Find Character Frequency
- [ ]  Find First Non-Repeating Character
- [ ]  Replace Characters
- [ ]  Remove Spaces
- [ ]  Sort Characters
- [ ]  Find Longest Word
- [ ]  Extract Numbers from a String

---

- [ ]  Reverse a String
- [ ]  Check Palindrome
- [ ]  Check Anagram
- [ ]  Count Vowels
- [ ]  Remove Duplicate Characters
- [ ]  Find Character Frequency
- [ ]  Reverse Words in a Sentence
- [ ]  Find Longest Word
- [ ]  Find First Non-Repeating Character
- [ ]  String Compression

### ARRAY

- [x]  Read and display array elements
- [x]  Find the sum of all elements
- [x]  Find the average of array elements
- [x]  Find the largest element
- [x]  Find the smallest element
- [x]  Count total elements in an array
- [x]  Display array elements in reverse order
- [x]  Copy one array into another
- [x]  Print even elements
- [x]  Print odd elements

---

- [x]  Linear Search
- [ ]  Binary Search
- [ ]  Search an element using user input
- [ ]  Count occurrences of an element
- [ ]  Find the first occurrence of an element
- [ ]  Find the last occurrence of an element
- [ ]  Search multiple elements
- [ ]  Find a missing number in an array
- [ ]  Check whether an element exists
- [ ]  Find duplicate elements

---

- [ ]  Sort array in ascending order
- [ ]  Sort array in descending order
- [ ]  Bubble Sort
- [ ]  Selection Sort
- [ ]  Insertion Sort
- [ ]  Sort string arrays alphabetically
- [ ]  Sort using Arrays.sort()
- [ ]  Sort only even numbers
- [ ]  Sort only odd numbers
- [ ]  Sort without using built-in functions

---

- [ ]  Add two matrices
- [ ]  Subtract two matrices
- [ ]  Multiply two matrices
- [ ]  Find transpose of a matrix
- [ ]  Calculate diagonal elements sum
- [ ]  Display upper triangular matrix
- [ ]  Display lower triangular matrix
- [ ]  Check identity matrix
- [ ]  Check symmetric matrix
- [ ]  Check sparse matrix

---

- [x]  Find the second largest element
- [ ]  Find the second smallest element
- [ ]  Remove duplicate elements
- [ ]  Merge two arrays
- [ ]  Split an array into two parts
- [ ]  Rotate an array to the left
- [ ]  Rotate an array to the right
- [ ]  Find common elements between arrays
- [ ]  Find a pair with a given sum
- [ ]  Find the frequency of each element

---

- [x]  Reverse an array
- [x]  Largest element in an array
- [x]  Smallest element in an array
- [ ]  Binary Search
- [ ]  Linear Search
- [ ]  Bubble Sort
- [ ]  Remove duplicates
- [ ]  Find missing numbers
- [ ]  Rotate arrays
- [ ]  Pair sum problem

### LINKED LIST (new)

- [ ]  Create and display a linked list
- [ ]  Insert a node (at beginning, end, and given position)
- [ ]  Delete a node (from beginning, end, and given position)
- [ ]  Search an element in a linked list
- [ ]  Count the number of nodes
- [ ]  Reverse a linked list (iterative)
- [ ]  Reverse a linked list (recursive)
- [ ]  Find the middle of a linked list
- [ ]  Detect a cycle in a linked list
- [ ]  Remove duplicates from a linked list
- [ ]  Merge two sorted linked lists
- [ ]  Check if a linked list is a palindrome

## Practice problems

### Question 1: rotate array

**Coding Q1: Rotate array**

**Problem:** Rotate an array to the right by k steps. Example: [1,2,3,4,5,6,7], k = 3 → [5,6,7,1,2,3,4].

**Approach:** Normalize k %= n. Reverse the whole array, reverse the first k elements, then reverse the rest. That yields the rotation in place.

**Complexity:** O(n) time, O(1) space

**Hexaware tip:** Restate the problem, sketch a brute-force idea, then tighten it. Call out edge cases (empty input, single element, overflow) before you write code.

### Question 2: first unique character

**Coding Q2: First unique character**

**Problem:** Find the first non-repeating character in a string and return its index, or -1 if none exists.

**Approach:** Count frequencies in one pass (hash map or array of 26 for lowercase). Second pass returns the first index with count 1.

**Complexity:** O(n) time

**Hexaware tip:** Restate the problem, sketch a brute-force idea, then tighten it. Call out edge cases (empty input, single element, overflow) before you write code.

### Question 3: stack with min

**Coding Q3: Stack with min**

**Problem:** Design a stack that supports push, pop, top, and getMin in average O(1) time.

**Approach:** Keep a parallel min-stack (or store pairs). When pushing, also push the new minimum. When popping, pop both stacks.

**Complexity:** O(1) per operation amortized

**Hexaware tip:** Restate the problem, sketch a brute-force idea, then tighten it. Call out edge cases (empty input, single element, overflow) before you write code.

### Question 4: maximum subarray sum

**Coding Q4: Maximum subarray sum (Kadane)**

**Problem:** Given an integer array, find the contiguous subarray with the largest sum and return that sum. Example: [-2,1,-3,4,-1,2,1,-5,4] → 6 (from [4,-1,2,1]).

**Approach:** Keep a running sum. If the running sum drops below 0, reset it to 0 before taking the next element (or track the best ending-here value). Track the global maximum as you scan once from left to right.

**Complexity:** O(n) time, O(1) extra space

**Hexaware tip:** Restate the problem, sketch a brute-force idea, then tighten it. Call out edge cases (empty input, single element, overflow) before you write code.

### Question 5: reverse a string in place

**Coding Q5: Reverse a string in place**

**Problem:** Given a mutable character array representing a string, reverse it in place without allocating another array of the same size.

**Approach:** Use two pointers at the start and end. Swap characters, then move inward until the pointers meet. Watch empty and single-character inputs.

**Complexity:** O(n) time, O(1) extra space

**Hexaware tip:** Restate the problem, sketch a brute-force idea, then tighten it. Call out edge cases (empty input, single element, overflow) before you write code.

### Question 6: check prime

**Coding Q6: Check prime**

**Problem:** Write a function that returns true if n is prime and false otherwise. Handle n < 2 correctly.

**Approach:** Return false for n < 2. Trial-divide from 2 to floor(sqrt(n)). If any divisor divides n evenly, it is composite; otherwise prime.

**Complexity:** O(√n) time

**Hexaware tip:** Restate the problem, sketch a brute-force idea, then tighten it. Call out edge cases (empty input, single element, overflow) before you write code.

### Question 7: valid parentheses

**Coding Q7: Valid parentheses**

**Problem:** Given a string containing only ‘()[]’, decide whether the brackets are balanced and correctly nested.

**Approach:** Scan left to right with a stack. Push opening brackets. On a closing bracket, the stack top must be the matching opener. At the end the stack must be empty.

**Complexity:** O(n) time, O(n) space

**Hexaware tip:** Restate the problem, sketch a brute-force idea, then tighten it. Call out edge cases (empty input, single element, overflow) before you write code.

### Question 8: two sum

**Coding Q8: Two Sum**

**Problem:** Given an array of integers and a target, return indices of two numbers that add up to the target. Assume exactly one solution and you may not use the same element twice.

**Approach:** Walk the array once. For each value x, check whether target − x was seen earlier in a hash map of value → index. If yes, return both indices; else store x.

**Complexity:** O(n) time, O(n) space

**Hexaware tip:** Restate the problem, sketch a brute-force idea, then tighten it. Call out edge cases (empty input, single element, overflow) before you write code.

### Question 9: longest substring without repeating characters

**Coding Q9: Longest substring without repeating characters**

**Problem:** Given a string s, find the length of the longest substring without repeating characters. Example: ‘abcabcbb’ → 3 (‘abc’).

**Approach:** Sliding window with a map (or last-seen index) of characters. Expand the right pointer; when a duplicate appears inside the window, move the left pointer past the previous occurrence.

**Complexity:** O(n) time

**Hexaware tip:** Restate the problem, sketch a brute-force idea, then tighten it. Call out edge cases (empty input, single element, overflow) before you write code.

### Question 10: merge overlapping intervals

**Coding Q10: Merge overlapping intervals**

**Problem:** Given a list of intervals [start, end], merge all overlapping intervals and return the non-overlapping set that covers the same ranges.

**Approach:** Sort by start time. Walk once, merging into the last interval in the result when the next start is ≤ current end; otherwise append a new interval.

**Complexity:** O(n log n) time from the sort

**Hexaware tip:** Restate the problem, sketch a brute-force idea, then tighten it. Call out edge cases (empty input, single element, overflow) before you write code.

## Pattern drill plan (2 weeks)

|Day|Drill|
|---|---|
|Mon|Arrays + hashing (2 problems)|
|Tue|Two pointers / sliding window|
|Wed|Stacks / strings|
|Thu|Trees or graphs basics|
|Fri|Timed mock (1-2 problems)|
|Sat|Re-solve misses cold|
|Sun|Explain your project out loud + rest|

## Comments & Suggestions

Nickname

Email

0/500

[](https://guides.github.com/features/mastering-markdown/)

No comment

Powered by [Twikoo](https://twikoo.js.org/) v1.7.19

## Related

[

Online assessment→



](https://placementpapers.app/hexaware/online-assessment/)[

Aptitude questions→



](https://placementpapers.app/hexaware/aptitude-questions/)[

Preparation guide→



](https://placementpapers.app/hexaware/preparation-guide/)[

Hexaware hub→



](https://placementpapers.app/hexaware/)

## Similar companies

[Mphasis](https://placementpapers.app/mphasis/) · [Virtusa](https://placementpapers.app/virtusa/) · [Coforge](https://placementpapers.app/coforge/) · [Persistent Systems](https://placementpapers.app/persistent/) · [CGI](https://placementpapers.app/cgi/)

![Anchal Katyal, Founder, placementpapers.app](https://placementpapers.app/anchal-katyal.png)

Written by[Anchal Katyal](https://placementpapers.app/author/)·Founder, placementpapers.app

Published on Apr 9, 2026·Updated on Jul 15, 2026

Practice Hexaware coding questions in the style students report for online assessments and technical interviews. Focus areas: Aptitude, basic coding, communication. Languages commonly allowed: Java, Python, C++.

Updated: October 2026 · [Logos provided by Logo.dev](https://logo.dev/)

[About](https://placementpapers.app/about/)[Author](https://placementpapers.app/author/)[Privacy](https://placementpapers.app/privacy-policy/)[Sitemap](https://placementpapers.app/sitemap-index.xml)[Terms](https://placementpapers.app/terms/)

© 2026 [KASP Digital LLC](https://kasp.ae/). All rights reserved.

[![Placement Papers - Featured on Startup Fame](https://startupfa.me/badge?t=offset&theme=default&r=square)](https://startupfa.me/s/placementpapers?utm_source=placementpapers.app)