# Hexaware GET / PGET Coding Questions — Pattern-Based Preparation Document

**Scope:** Questions and patterns reported in Hexaware GET, PGET, and SPGET drives from roughly 2021–2025, based on publicly available interview experiences and preparation pages from GeeksforGeeks, PrepInsta, AmbitionBox, FreshersNow, and LinkedIn-shared experiences.

**Important:** No company publishes an official exhaustive question bank. This document combines **actually reported questions** with the **patterns they represent**. If you can solve every problem below without hints, you will be well prepared for the Hexaware coding round and live-coding interview.

---

## 1. Pattern analysis from previous years

## Reported process patterns

- GET drives commonly include aptitude + domain/pseudocode, communication assessment, technical interview, and HR. [GfG GET/PGET 2024](https://www.geeksforgeeks.org/interview-experiences/hexaware-technologies-limited-interview-experience-for-get-and-pget-on-campus-2024/)
    
- PGET usually adds a coding assessment; reported formats include 2 coding questions, sometimes with an SQL query. [FreshersNow](https://www.freshersnow.com/hexaware-technologies-recruitment/), [AmbitionBox](https://www.ambitionbox.com/interviews/hexaware-technologies-interview-questions/graduate-trainee)
    
- One SPGET/GET-PGET report described a 90-minute coding test with **2 DSA questions + 1 SQL query**. [GfG SPGET 2023–24](https://www.geeksforgeeks.org/hexaware-interview-experience-on-campus-spget2023-2024/)
    
- Technical interviews often include live coding, OOP, SQL/DBMS, pseudocode, DSA basics, and project cross-questioning. [GfG PGET 2022](https://www.geeksforgeeks.org/hexaware-interview-experience-for-pget-on-campus/), [GfG GET 2023](https://www.geeksforgeeks.org/interview-experiences/hexaware-technologies-experience-for-get-on-campus-2023/)
    

## Frequency of topics

|Rank|Topic|Evidence / pattern|
|---|---|---|
|1|Arrays|2024 PGET coding round reportedly had two array questions; 2025 PGET had array-sum/removal logic; SPGET asked third-largest array element. [GfG PGET 2024/2025, SPGET]|
|2|Strings|Reported questions include odd-length word selection, minimum-frequency character, substring/lexicographic string, vowel/word-count logic. [PrepInsta Hexaware coding, GfG PGET 2023]|
|3|Number / math logic|Prime numbers, Fibonacci, Armstrong, digit operations, sequence sums. [GfG PGET 2022, PrepInsta GET questions]|
|4|Sorting / searching|Bubble sort implementation and tracing, binary search, third-largest without sorting. [GfG PGET 2023, SPGET 2023–24]|
|5|Linked list / stack / queue|Reported in PGET interview/coding-topic lists; stack vs queue and linked-list concepts are common. [AmbitionBox PGET, GfG PGET 2023]|
|6|Hashing / sets / maps|Duplicate counting, frequency counting, minimum-frequency character. [PrepInsta Hexaware coding]|
|7|Recursion|Fibonacci using recursion; basic recursive number/string problems. [SPGET 2023–24, PrepInsta GET]|
|8|Prefix sum / sliding window / greedy|Stock profit, maximum of minimums in subarrays, frog-between-stones. [PrepInsta Hexaware coding]|
|9|SQL|One SQL query may appear in coding round; joins, update, create/insert, Nth-highest salary in interviews. [SPGET 2023–24, GfG PGET 2022/2023]|
|10|Trees / graphs / DP|Low frequency for coding; graph applications have been asked conceptually. Prepare basics only. [GfG PGET 2024]|

## Main conclusion

Hexaware’s coding questions are usually **implementation-oriented**, not hard algorithmic LeetCode-style problems. The dominant pattern is:

1. Read input carefully.
    
2. Apply array/string/number logic.
    
3. Handle edge cases.
    
4. Produce correct output.
    

For PGET, expect **2 problems**, often one easy and one easy-to-medium. For GET, expect simpler live-coding questions in the interview.

---

## 2. Previously reported Hexaware questions

Solve these first. They are directly reported or closely derived from reported Hexaware questions.

## A. Array questions

1. Find the largest and smallest element in an array.
    
2. Find the second-largest element without sorting.
    
3. Find the third-largest element without using a sort function. **[Directly asked — SPGET 2023–24]**
    
4. Reverse an array.
    
5. Rotate an array by K positions, left and right.
    
6. Remove duplicates from an array.
    
7. Count duplicate elements.
    
    - Reported PrepInsta variant: given roll numbers, find how many repeated emails must be deleted. **[PrepInsta Hexaware coding]**
        
8. Find the missing number from 1 to N.
    
9. Find the majority element / element appearing more than N/2 times.
    
10. Find the sum of all elements and average of an array.
    
11. Separate even and odd numbers.
    
12. Move all zeros to the end.
    
13. Merge two sorted arrays.
    
14. Find whether two arrays are equal after sorting.
    
15. Find the pair with a given sum.
    
16. Find all pairs with a given sum.
    
17. Find the maximum difference such that the larger element comes after the smaller element.
    
18. Maximum profit from stock prices — buy low, sell high.
    
    - Reported PrepInsta Hexaware question: calculate maximum profit from daily prices. **[PrepInsta Hexaware coding]**
        
19. Maximum subarray sum — Kadane’s algorithm.
    
    - Used in the PrepInsta stock-profit solution pattern. **[PrepInsta Hexaware coding]**
        
20. Maximum of minimums for every contiguous subarray of length K.
    
    - Reported PrepInsta Hexaware question. **[PrepInsta Hexaware coding]**
        
21. Prefix-sum problems: range sum queries, count elements in a range.
    
22. Matrix basics: diagonal sum, transpose, row-wise/column-wise sum, rotate matrix.
    

## B. String questions

1. Reverse a string.
    
2. Reverse words in a sentence.
    
3. Check whether a string is a palindrome.
    
4. Check whether a number is a palindrome. **[Directly asked — PrepInsta GET]**
    
5. Count vowels, consonants, digits, spaces, and special characters.
    
6. Count frequency of each character.
    
7. Find the first non-repeating character.
    
8. Find the minimum-frequency character; if tied, return the first occurring one.
    
    - Reported PrepInsta Hexaware question. **[PrepInsta Hexaware coding]**
        
9. Check whether two strings are anagrams.
    
10. Remove duplicate characters from a string.
    
11. Find the longest word in a sentence.
    
12. Find the word with odd length and maximum length; if none exists, print “Better luck next time”.
    
    - Reported PrepInsta Hexaware question. **[PrepInsta Hexaware coding]**
        
13. Count words in a sentence.
    
14. Count words without vowels.
    
    - Reported Hexaware PGET 2023 coding question. **[GfG PGET 2023]**
        
15. Count words of a given length K.
    
    - Reported Hexaware PGET 2023 coding question. **[GfG PGET 2023]**
        
16. Convert case: uppercase to lowercase and vice versa.
    
17. Toggle case of each character.
    
18. Check whether a string contains only digits.
    
19. Find the lexicographically largest substring/suffix.
    
    - Reported PrepInsta Hexaware question: find the last student ID generated from substrings. **[PrepInsta Hexaware coding]**
        
20. String grouping: split a string by separators such as `@` or `$` and find the largest group.
    
    - Reported PrepInsta Hexaware question. **[PrepInsta Hexaware coding]**
        
21. Check whether one string is a rotation of another.
    
22. Compress a string, e.g., `aaabbc` → `a3b2c1`.
    

## C. Number and math questions

1. Print prime numbers from 1 to 100. **[Directly asked — GfG PGET 2022]**
    
2. Check whether a number is prime.
    
3. Print all primes in a given range.
    
4. Print the Fibonacci series up to N terms. **[Directly asked — PrepInsta GET]**
    
5. Print Fibonacci series using recursion. **[Directly asked — SPGET 2023–24]**
    
6. Check Armstrong number.
    
7. Print Armstrong numbers in a range. **[Directly asked — PrepInsta GET]**
    
8. Find factorial of a number.
    
9. Find GCD and LCM of two numbers.
    
10. Reverse a number.
    
11. Count digits in a number.
    
12. Sum of digits of a number.
    
13. Product of digits of a number.
    
14. Check perfect number.
    
15. Check strong number.
    
16. Check automorphic number.
    
17. Check whether a number is a power of two.
    
18. Swap two numbers without a third variable.
    
19. Find the sum of a sequence that increases from `i` to `j`, then decreases to `k`.
    
    - Reported PrepInsta Hexaware question. **[PrepInsta Hexaware coding]**
        
20. Find the minimum subset sum needed to make one side stronger than the other.
    
    - Reported PrepInsta Hexaware question: vampire-power problem. **[PrepInsta Hexaware coding]**
        

## D. Recursion questions

1. Factorial using recursion.
    
2. Fibonacci using recursion. **[Directly asked — SPGET 2023–24]**
    
3. Sum of first N natural numbers using recursion.
    
4. Sum of digits using recursion.
    
5. Reverse a string using recursion.
    
6. Check palindrome using recursion.
    
7. Print numbers from 1 to N and N to 1 using recursion.
    
8. Power of a number using recursion.
    
9. Binary search using recursion.
    
10. Tower of Hanoi — optional, for confidence.
    

## E. Sorting and searching

1. Implement bubble sort and explain each pass.
    
    - Directly asked in a Hexaware PGET interview. **[GfG PGET 2023]**
        
2. Implement selection sort.
    
3. Implement insertion sort.
    
4. Implement merge sort.
    
5. Implement quicksort — optional for PGET.
    
6. Linear search.
    
7. Binary search.
    
8. Find first and last occurrence of an element in a sorted array.
    
9. Find the floor and ceiling of a number in a sorted array.
    
10. Search in a rotated sorted array — optional, medium level.
    

## F. Linked list, stack, queue

1. Create and traverse a singly linked list.
    
2. Insert at beginning, end, and a given position.
    
3. Delete a node by value or position.
    
4. Reverse a singly linked list.
    
5. Find the middle element of a linked list.
    
6. Detect a cycle in a linked list.
    
7. Implement a stack using an array.
    
8. Implement a stack using a linked list.
    
9. Check balanced parentheses using a stack.
    
10. Implement a queue using an array.
    
11. Implement a queue using two stacks.
    
12. Explain stack vs queue with real-life examples.
    
    - Stack vs queue was asked in a Hexaware PGET interview. **[GfG PGET 2024]**
        

## G. Hashing / maps / sets

1. Count frequency of array elements.
    
2. Count frequency of characters in a string.
    
3. Find duplicates in an array.
    
4. Remove duplicates from an array/string.
    
5. Find the first non-repeating character.
    
6. Find the majority element.
    
7. Check anagram using a frequency map.
    
8. Union and intersection of two arrays.
    
9. Count distinct elements.
    
10. Find the element with the highest and lowest frequency.
    

## H. Prefix sum, sliding window, greedy

1. Prefix sum of an array.
    
2. Range sum query using prefix sum.
    
3. Maximum sum subarray of size K — sliding window.
    
4. Minimum sum subarray of size K.
    
5. Longest substring without repeating characters — optional medium.
    
6. Frog-between-stones counting problem using prefix sums.
    
    - Reported PrepInsta Hexaware question. **[PrepInsta Hexaware coding]**
        
7. Minimum number of elements needed to exceed the remaining total.
    
    - Reported PrepInsta Hexaware vampire-power question. **[PrepInsta Hexaware coding]**
        

## I. Pseudocode-style coding

These are especially important because Hexaware domain tests have included pseudocode and bitwise operations.

1. Predict output of nested loops.
    
2. Trace recursion output.
    
3. Bitwise AND, OR, XOR, left shift, right shift.
    
    - Bitwise operations were reported as a major pseudocode topic. **[GfG GET/PGET 2024]**
        
4. Check odd/even using bitwise operator.
    
5. Swap two numbers using XOR.
    
6. Count set bits in a number.
    
7. Check whether the Kth bit is set.
    
8. Find the unique element when every other element appears twice.
    
9. Convert decimal to binary and binary to decimal.
    
10. Operator precedence and short-circuit evaluation questions.
    

## J. SQL questions for the coding/interview round

1. Create a table and insert rows. **[Directly asked — GfG GET 2023]**
    
2. Update a person’s name from A to B. **[Directly asked — GfG PGET 2022]**
    
3. Select all employees whose salary is greater than a value.
    
4. Find the second-highest salary.
    
5. Find the Nth-highest salary.
    
6. Find employees with salary above the department average.
    
7. Find employees who do not belong to any department using LEFT JOIN.
    
8. Find department-wise maximum, minimum, and average salary.
    
9. Explain and write INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN.
    
10. Difference between DELETE, TRUNCATE, and DROP. **[Directly asked — SPGET 2023–24]**
    
11. Difference between DDL and DML. **[Directly asked — SPGET 2023–24]**
    
12. Write a query using GROUP BY and HAVING.
    

---

## 3. GET-specific minimum list

For GET, prioritize these 30 problems. They cover nearly all reported GET live-coding patterns.

1. Reverse a string
    
2. Palindrome string
    
3. Palindrome number
    
4. Prime number
    
5. Prime numbers from 1 to 100
    
6. Fibonacci series
    
7. Fibonacci using recursion
    
8. Armstrong number
    
9. Armstrong numbers in a range
    
10. Factorial
    
11. Sum of digits
    
12. Reverse a number
    
13. Count vowels and consonants
    
14. Largest element in an array
    
15. Second-largest element
    
16. Remove duplicates from array
    
17. Sort an array using bubble sort
    
18. Linear search
    
19. Binary search
    
20. Swap two numbers
    
21. Print patterns: triangle, pyramid, number pyramid
    
22. Matrix addition and transpose
    
23. Implement pointers in C/C++
    
    - Directly asked in a Hexaware GET interview. **[GfG GET 2023]**
        
24. Use of `this` keyword in C++/Java
    
    - Directly asked in a Hexaware GET interview. **[GfG GET 2023]**
        
25. Print first and last name without loop/recursion
    
    - Directly asked in a Hexaware GET interview. **[GfG GET 2023]**
        
26. Create and insert into a SQL table
    
    - Directly asked in a Hexaware GET interview. **[GfG GET 2023]**
        
27. SQL UPDATE query
    
28. Basic SELECT with WHERE
    
29. Basic JOIN query
    
30. Simple OOP program demonstrating inheritance or polymorphism
    

---

## 4. PGET-specific priority list

For PGET, solve the GET list plus these 40 problems.

## Arrays — medium

1. Kadane’s maximum subarray sum
    
2. Maximum profit from stock prices
    
3. Maximum of minimums in every subarray of size K
    
4. Prefix sum and range-sum query
    
5. Rotate array by K
    
6. Merge overlapping intervals — optional
    
7. Dutch national flag / sort 0s, 1s, 2s
    
8. Majority element using Moore’s voting
    
9. Longest consecutive sequence — optional
    
10. Subarray with given sum using prefix sum/hash map
    

## Strings — medium

1. Longest word in a sentence
    
2. Longest common prefix
    
3. String compression
    
4. Check anagram
    
5. Group anagrams — optional
    
6. First non-repeating character
    
7. Minimum-frequency character with first-occurrence tie-break
    
8. Longest substring without repeating characters
    
9. Lexicographically largest suffix/substring
    
10. Count words by condition: length, vowels, separators
    

## Linked list / stack / queue — medium

1. Reverse linked list
    
2. Middle of linked list
    
3. Detect cycle
    
4. Merge two sorted linked lists
    
5. Implement stack with min operation — optional
    
6. Valid parentheses
    
7. Next greater element using stack
    
8. Queue using two stacks
    
9. Sliding-window maximum — optional
    
10. Implement circular queue
    

## Hashing / greedy / prefix — medium

1. Two-sum using hash map
    
2. Count distinct elements in every window of size K
    
3. Longest subarray with sum K
    
4. Minimum number of coins/elements to reach a target
    
5. Activity selection — optional
    
6. Fractional knapsack — optional
    
7. Job sequencing — optional
    
8. Prefix-sum range counting
    
9. Frog-between-stones problem
    
10. Duplicate-email deletion count
    

## SQL — PGET level

1. Second-highest salary
    
2. Nth-highest salary
    
3. Department-wise highest salary
    
4. Employees earning more than manager
    
5. Employees without department
    
6. Duplicate rows detection
    
7. Delete duplicate rows
    
8. JOIN + GROUP BY + HAVING combined query
    
9. Self JOIN
    
10. CASE WHEN query
    

---

## 5. Tree, graph, and DP: exact preparation

## Trees — prepare concepts, not hard coding

- Binary tree vs binary search tree
    
- Tree traversals: inorder, preorder, postorder
    
- Height and depth
    
- Level-order traversal
    
- Lowest common ancestor — optional
    
- Real-life uses: file systems, DOM, expression trees
    

## Graphs — prepare concepts and one simple implementation

- Graph vs tree
    
- Directed vs undirected graph
    
- BFS and DFS
    
- Adjacency list vs adjacency matrix
    
- Applications: maps, social networks, dependency resolution
    
- A Hexaware PGET 2024 interview reportedly asked about graph applications. **[GfG PGET 2024]**
    

## Dynamic programming — minimum only

- What DP means
    
- Overlapping subproblems
    
- Memoization vs tabulation
    
- Fibonacci using DP
    
- Climbing stairs
    
- Do not prioritize 0/1 knapsack, LIS, LCS, or hard DP unless you have extra time.
    

---

## 6. Reference list

## GeeksforGeeks interview experiences

- Hexaware PGET On-Campus 2025: coding questions on sequence and array-sum removal logic.  
    [https://www.geeksforgeeks.org/interview-experiences/hexaware-technologies-interview-experience-for-pget-on-campus-2025/](https://www.geeksforgeeks.org/interview-experiences/hexaware-technologies-interview-experience-for-pget-on-campus-2025/)
    
- Hexaware PGET On-Campus 2024: two array-based coding questions; Fibonacci, Armstrong, OOP, SQL, stack/queue, graph applications.  
    [https://www.geeksforgeeks.org/interview-experiences/hexaware-interview-experience-for-pget-on-campus-2024/](https://www.geeksforgeeks.org/interview-experiences/hexaware-interview-experience-for-pget-on-campus-2024/)
    
- Hexaware PGET On-Campus 2023: vowel-word and word-length coding questions; bubble sort; array/vector; SQL; OOP.  
    [https://www.geeksforgeeks.org/interview-experiences/hexaware-interview-experience-for-pget-2023/](https://www.geeksforgeeks.org/interview-experiences/hexaware-interview-experience-for-pget-2023/)
    
- Hexaware PGET 2023: SQL, project, bubble sort.  
    [https://www.geeksforgeeks.org/hexaware-technologies-interview-experience-for-pget/](https://www.geeksforgeeks.org/hexaware-technologies-interview-experience-for-pget/)
    
- Hexaware PGET 2022: prime numbers 1–100; SQL update; OOP; SDLC.  
    [https://www.geeksforgeeks.org/hexaware-interview-experience-for-pget-on-campus/](https://www.geeksforgeeks.org/hexaware-interview-experience-for-pget-on-campus/)
    
- Hexaware GET 2023: pointers, `this` keyword, name printing without loop/recursion, SQL create/insert.  
    [https://www.geeksforgeeks.org/interview-experiences/hexaware-technologies-experience-for-get-on-campus-2023/](https://www.geeksforgeeks.org/interview-experiences/hexaware-technologies-experience-for-get-on-campus-2023/)
    
- Hexaware GET/PGET 2024: pseudocode and bitwise operations, communication, HR.  
    [https://www.geeksforgeeks.org/interview-experiences/hexaware-technologies-limited-interview-experience-for-get-and-pget-on-campus-2024/](https://www.geeksforgeeks.org/interview-experiences/hexaware-technologies-limited-interview-experience-for-get-and-pget-on-campus-2024/)
    
- Hexaware SPGET 2023–24: 2 DSA questions + 1 SQL query; third-largest array element; Fibonacci recursion; polymorphism.  
    [https://www.geeksforgeeks.org/hexaware-interview-experience-on-campus-spget2023-2024/](https://www.geeksforgeeks.org/hexaware-interview-experience-on-campus-spget2023-2024/)
    

## PrepInsta

- Hexaware coding questions and sample problems: odd-length word, stock profit, frog-between-stones, vampire-power, string grouping, minimum-frequency character, sequence sum, duplicate deletion, lexicographic substring, maximum of minimums.  
    [https://prepinsta.com/hexaware/coding/](https://prepinsta.com/hexaware/coding/)
    
- Hexaware GET interview questions: Fibonacci, Armstrong range, palindrome number, SQL and OOP questions.  
    [https://prepinsta.com/hexaware/graduate-engineer-trainee/interview-questions/](https://prepinsta.com/hexaware/graduate-engineer-trainee/interview-questions/)
    

## AmbitionBox

- Hexaware Graduate Trainee interview questions and experiences: arrays, strings, linked list, stacks, queues; coding test with one easy and one easy-to-medium question.  
    [https://www.ambitionbox.com/interviews/hexaware-technologies-interview-questions/graduate-trainee](https://www.ambitionbox.com/interviews/hexaware-technologies-interview-questions/graduate-trainee)
    
- Hexaware PGET interview questions and experiences.  
    [https://www.ambitionbox.com/interviews/hexaware-technologies-interview-questions/pget](https://www.ambitionbox.com/interviews/hexaware-technologies-interview-questions/pget)
    
- Hexaware general interview questions and process reports.  
    [https://www.ambitionbox.com/interviews/hexaware-technologies-interview-questions](https://www.ambitionbox.com/interviews/hexaware-technologies-interview-questions)
    

## FreshersNow

- Hexaware placement papers and selection process for GET/PGET.  
    [https://www.freshersnow.com/hexaware-placement-papers/](https://www.freshersnow.com/hexaware-placement-papers/)
    
- Hexaware interview questions for freshers: C, C++, Java, DBMS, DSA, OS, resume-based questions.  
    [https://www.freshersnow.com/hexaware-interview-questions-for-freshers/](https://www.freshersnow.com/hexaware-interview-questions-for-freshers/)
    
- Hexaware off-campus recruitment process for GET/PGET.  
    [https://www.freshersnow.com/hexaware-technologies-recruitment/](https://www.freshersnow.com/hexaware-technologies-recruitment/)
    

## LinkedIn

Search LinkedIn for these exact phrases to find candidate posts and shared experiences:

- `Hexaware PGET interview experience coding questions`
    
- `Hexaware GET interview experience coding questions`
    
- `Hexaware PGET 2024 coding round`
    
- `Hexaware PGET 2025 interview experience`
    
- `Hexaware array string coding question`
    
- `Hexaware Fibonacci Armstrong interview`
    
- `Hexaware SQL query interview`
    

LinkedIn posts are useful for recent campus-specific experiences, but treat them as supplementary evidence because they are often brief and cannot always be independently verified.

---

## 7. Final practice rule

Do not just read solutions. For every question:

1. Write the approach in 2–3 lines.
    
2. Code it without help.
    
3. Test with normal, empty, single-element, negative, duplicate, and boundary inputs.
    
4. State time and space complexity.
    
5. Re-solve it after 3 days.
    

If you complete this document—especially the **directly reported questions** and the **GET/PGET priority lists**—you will cover the realistic Hexaware GET and PGET coding-question space far better than randomly solving LeetCode.