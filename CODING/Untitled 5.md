---

title: Java DSA Practice Notes

tags: [java, dsa, placement, strings, arrays, linked-list]

---

  

# Java DSA Practice Notes

  

> Every question from the checklist, with short, clean, efficient Java.

> Each snippet is a **method**. Paste it inside `public class Main` and call it from `main`.

  

**Contents**

- [[#Template]]

- [[#1. Strings]]

- [[#2. Arrays: Basics]]

- [[#3. Arrays: Searching]]

- [[#4. Arrays: Sorting]]

- [[#5. Arrays: Matrix]]

- [[#6. Arrays: Other Operations]]

- [[#7. Linked List]]

- [[#8. Practice Problems Q1 to Q10]]

- [[#9. Repeated Items (cross-reference)]]

  

---

  

## Template

  

```java

import java.util.*;

  

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String s = sc.nextLine();

        System.out.println(solve(s));   // call any method below

    }

  

    // paste method here

}

```

  

---

  

## 1. Strings

  

### 1.1 Reverse a String

```java

static String reverse(String s) {

    return new StringBuilder(s).reverse().toString();

}

```

Time O(n), Space O(n)

  

### 1.2 Check Palindrome

```java

static boolean isPalindrome(String s) {

    int i = 0, j = s.length() - 1;

    while (i < j) {

        if (s.charAt(i++) != s.charAt(j--)) return false;

    }

    return true;

}

```

Two pointers, no extra string. Time O(n), Space O(1)

  

### 1.3 Count Vowels

```java

static int countVowels(String s) {

    int count = 0;

    for (char c : s.toLowerCase().toCharArray())

        if ("aeiou".indexOf(c) != -1) count++;

    return count;

}

```

  

### 1.4 Count Consonants

```java

static int countConsonants(String s) {

    int count = 0;

    for (char c : s.toLowerCase().toCharArray())

        if (Character.isLetter(c) && "aeiou".indexOf(c) == -1) count++;

    return count;

}

```

  

### 1.5 Remove Duplicate Characters

```java

static String removeDuplicates(String s) {

    StringBuilder sb = new StringBuilder();

    boolean[] seen = new boolean[256];

    for (char c : s.toCharArray()) {

        if (!seen[c]) {

            seen[c] = true;

            sb.append(c);

        }

    }

    return sb.toString();

}

```

Keeps first occurrence, original order. Time O(n)

  

### 1.6 Find Duplicate Characters

```java

static void findDuplicates(String s) {

    int[] freq = new int[256];

    for (char c : s.toCharArray()) freq[c]++;

    for (int i = 0; i < 256; i++)

        if (freq[i] > 1) System.out.print((char) i + " ");

}

```

  

### 1.7 Check Anagram

```java

static boolean isAnagram(String a, String b) {

    if (a.length() != b.length()) return false;

    int[] count = new int[256];

    for (int i = 0; i < a.length(); i++) {

        count[a.charAt(i)]++;

        count[b.charAt(i)]--;

    }

    for (int c : count) if (c != 0) return false;

    return true;

}

```

Time O(n), Space O(1). Use `toLowerCase()` first if case should be ignored.

  

### 1.8 Count Words

```java

static int countWords(String s) {

    s = s.trim();

    return s.isEmpty() ? 0 : s.split("\\s+").length;

}

```

  

### 1.9 Find Character Frequency

```java

static void frequency(String s) {

    Map<Character, Integer> map = new LinkedHashMap<>();

    for (char c : s.toCharArray())

        map.put(c, map.getOrDefault(c, 0) + 1);

    for (Map.Entry<Character, Integer> e : map.entrySet())

        System.out.println(e.getKey() + " = " + e.getValue());

}

```

`LinkedHashMap` prints in the order characters first appeared.

  

### 1.10 Find First Non-Repeating Character

```java

static char firstNonRepeating(String s) {

    int[] freq = new int[256];

    for (char c : s.toCharArray()) freq[c]++;

    for (char c : s.toCharArray())

        if (freq[c] == 1) return c;

    return '\0';   // none found

}

```

Two passes. Time O(n), Space O(1)

  

### 1.11 Replace Characters

```java

static String replaceChar(String s, char oldCh, char newCh) {

    return s.replace(oldCh, newCh);

}

```

  

### 1.12 Remove Spaces

```java

static String removeSpaces(String s) {

    return s.replaceAll("\\s", "");

}

```

  

### 1.13 Sort Characters

```java

static String sortChars(String s) {

    char[] ch = s.toCharArray();

    Arrays.sort(ch);

    return new String(ch);

}

```

Time O(n log n)

  

### 1.14 Find Longest Word

```java

static String longestWord(String s) {

    String longest = "";

    for (String w : s.trim().split("\\s+"))

        if (w.length() > longest.length()) longest = w;

    return longest;

}

```

  

### 1.15 Extract Numbers from a String

```java

// All digits: "a1b23" -> "123"

static String extractDigits(String s) {

    StringBuilder sb = new StringBuilder();

    for (char c : s.toCharArray())

        if (Character.isDigit(c)) sb.append(c);

    return sb.toString();

}

  

// Whole numbers: "a12b345c6" -> 12, 345, 6

static List<Integer> extractNumbers(String s) {

    List<Integer> list = new ArrayList<>();

    for (String part : s.split("\\D+"))

        if (!part.isEmpty()) list.add(Integer.parseInt(part));

    return list;

}

```

  

### 1.16 Reverse Words in a Sentence

```java

static String reverseWords(String s) {

    String[] w = s.trim().split("\\s+");

    Collections.reverse(Arrays.asList(w));

    return String.join(" ", w);

}

```

"I love Java" gives "Java love I"

  

### 1.17 String Compression

```java

static String compress(String s) {

    if (s.isEmpty()) return s;

    StringBuilder sb = new StringBuilder();

    int count = 1;

    for (int i = 1; i <= s.length(); i++) {

        if (i < s.length() && s.charAt(i) == s.charAt(i - 1)) {

            count++;

        } else {

            sb.append(s.charAt(i - 1)).append(count);

            count = 1;

        }

    }

    return sb.toString();

}

```

"aabcccc" gives "a2b1c4". Time O(n)

  

---

  

## 2. Arrays: Basics

  

One program covers the whole list.

  

```java

static void basics(int[] a) {

    int n = a.length;

    int sum = 0, max = a[0], min = a[0];

  

    for (int x : a) {

        sum += x;

        max = Math.max(max, x);

        min = Math.min(min, x);

    }

  

    System.out.println("Elements: " + Arrays.toString(a));             // display

    System.out.println("Count: " + n);                                  // total elements

    System.out.println("Sum: " + sum);

    System.out.println("Average: " + (double) sum / n);

    System.out.println("Largest: " + max);

    System.out.println("Smallest: " + min);

  

    System.out.print("Reverse: ");                                      // reverse order

    for (int i = n - 1; i >= 0; i--) System.out.print(a[i] + " ");

  

    int[] copy = Arrays.copyOf(a, n);                                   // copy array

    System.out.println("\nCopy: " + Arrays.toString(copy));

  

    System.out.print("Even: ");

    for (int x : a) if (x % 2 == 0) System.out.print(x + " ");

    System.out.print("\nOdd: ");

    for (int x : a) if (x % 2 != 0) System.out.print(x + " ");

}

```

  

Reading the array from the user:

```java

static int[] readArray(Scanner sc) {

    int n = sc.nextInt();

    int[] a = new int[n];

    for (int i = 0; i < n; i++) a[i] = sc.nextInt();

    return a;

}

```

  

---

  

## 3. Arrays: Searching

  

### 3.1 Linear Search

```java

static int linearSearch(int[] a, int key) {

    for (int i = 0; i < a.length; i++)

        if (a[i] == key) return i;

    return -1;

}

```

Time O(n)

  

### 3.2 Binary Search

```java

static int binarySearch(int[] a, int key) {   // array must be sorted

    int low = 0, high = a.length - 1;

    while (low <= high) {

        int mid = low + (high - low) / 2;

        if (a[mid] == key) return mid;

        if (a[mid] < key) low = mid + 1;

        else high = mid - 1;

    }

    return -1;

}

```

Time O(log n). `low + (high - low) / 2` avoids overflow.

  

### 3.3 Search an Element Using User Input

```java

Scanner sc = new Scanner(System.in);

int n = sc.nextInt();

int[] a = new int[n];

for (int i = 0; i < n; i++) a[i] = sc.nextInt();

int key = sc.nextInt();

  

int idx = linearSearch(a, key);

System.out.println(idx == -1 ? "Not found" : "Found at index " + idx);

```

  

### 3.4 Count Occurrences of an Element

```java

static int countOccurrences(int[] a, int key) {

    int count = 0;

    for (int x : a) if (x == key) count++;

    return count;

}

```

  

### 3.5 Find the First Occurrence

```java

static int firstOccurrence(int[] a, int key) {

    for (int i = 0; i < a.length; i++)

        if (a[i] == key) return i;

    return -1;

}

```

  

### 3.6 Find the Last Occurrence

```java

static int lastOccurrence(int[] a, int key) {

    for (int i = a.length - 1; i >= 0; i--)

        if (a[i] == key) return i;

    return -1;

}

```

  

### 3.7 Search Multiple Elements

```java

static void searchMultiple(int[] a, int[] keys) {

    Set<Integer> set = new HashSet<>();

    for (int x : a) set.add(x);

    for (int k : keys)

        System.out.println(k + (set.contains(k) ? " found" : " not found"));

}

```

HashSet makes each lookup O(1).

  

### 3.8 Find a Missing Number

```java

static int missingNumber(int[] a) {   // array holds 1..n with one number missing

    int n = a.length + 1;

    int expected = n * (n + 1) / 2;

    int sum = 0;

    for (int x : a) sum += x;

    return expected - sum;

}

```

Time O(n), Space O(1)

  

### 3.9 Check Whether an Element Exists

```java

static boolean exists(int[] a, int key) {

    for (int x : a) if (x == key) return true;

    return false;

}

```

  

### 3.10 Find Duplicate Elements

```java

static void findDuplicates(int[] a) {

    Set<Integer> seen = new HashSet<>();

    Set<Integer> printed = new HashSet<>();

    for (int x : a) {

        if (!seen.add(x) && printed.add(x))

            System.out.print(x + " ");

    }

}

```

`add` returns false when the value is already present.

  

---

  

## 4. Arrays: Sorting

  

### 4.1 Sort Ascending

```java

static void sortAsc(int[] a) {

    Arrays.sort(a);

}

```

  

### 4.2 Sort Descending

```java

static void sortDesc(Integer[] a) {          // must be Integer[], not int[]

    Arrays.sort(a, Collections.reverseOrder());

}

```

  

### 4.3 Bubble Sort

```java

static void bubbleSort(int[] a) {

    for (int i = 0; i < a.length - 1; i++) {

        boolean swapped = false;

        for (int j = 0; j < a.length - 1 - i; j++) {

            if (a[j] > a[j + 1]) {

                int t = a[j]; a[j] = a[j + 1]; a[j + 1] = t;

                swapped = true;

            }

        }

        if (!swapped) break;   // already sorted

    }

}

```

Best O(n), Worst O(n^2)

  

### 4.4 Selection Sort

```java

static void selectionSort(int[] a) {

    for (int i = 0; i < a.length - 1; i++) {

        int min = i;

        for (int j = i + 1; j < a.length; j++)

            if (a[j] < a[min]) min = j;

        int t = a[i]; a[i] = a[min]; a[min] = t;

    }

}

```

O(n^2), at most n-1 swaps.

  

### 4.5 Insertion Sort

```java

static void insertionSort(int[] a) {

    for (int i = 1; i < a.length; i++) {

        int key = a[i], j = i - 1;

        while (j >= 0 && a[j] > key) {

            a[j + 1] = a[j];

            j--;

        }

        a[j + 1] = key;

    }

}

```

Best O(n), Worst O(n^2)

  

### 4.6 Sort String Arrays Alphabetically

```java

static void sortStrings(String[] s) {

    Arrays.sort(s);                                  // case-sensitive

    // Arrays.sort(s, String.CASE_INSENSITIVE_ORDER);  // ignore case

}

```

  

### 4.7 Sort Using Arrays.sort()

```java

int[] a = {5, 2, 9, 1};

Arrays.sort(a);

System.out.println(Arrays.toString(a));   // [1, 2, 5, 9]

```

  

### 4.8 and 4.9 Sort Only Even / Only Odd Numbers

Sorted values go back into the positions of the same kind. Other numbers stay where they are.

```java

static void sortOnly(int[] a, boolean even) {

    List<Integer> list = new ArrayList<>();

    for (int x : a)

        if ((x % 2 == 0) == even) list.add(x);

  

    Collections.sort(list);

  

    int k = 0;

    for (int i = 0; i < a.length; i++)

        if ((a[i] % 2 == 0) == even) a[i] = list.get(k++);

}

// sortOnly(a, true)  -> sort evens

// sortOnly(a, false) -> sort odds

```

`{5, 2, 8, 3, 4}` with evens gives `{5, 2, 4, 3, 8}`

  

### 4.10 Sort Without Using Built-in Functions

Use any manual sort: [[#4.3 Bubble Sort]], [[#4.4 Selection Sort]] or [[#4.5 Insertion Sort]].

  

---

  

## 5. Arrays: Matrix

  

### 5.1 Add Two Matrices

```java

static int[][] add(int[][] a, int[][] b) {

    int r = a.length, c = a[0].length;

    int[][] res = new int[r][c];

    for (int i = 0; i < r; i++)

        for (int j = 0; j < c; j++)

            res[i][j] = a[i][j] + b[i][j];

    return res;

}

```

  

### 5.2 Subtract Two Matrices

```java

static int[][] subtract(int[][] a, int[][] b) {

    int r = a.length, c = a[0].length;

    int[][] res = new int[r][c];

    for (int i = 0; i < r; i++)

        for (int j = 0; j < c; j++)

            res[i][j] = a[i][j] - b[i][j];

    return res;

}

```

  

### 5.3 Multiply Two Matrices

```java

static int[][] multiply(int[][] a, int[][] b) {   // a: r x n, b: n x c

    int r = a.length, n = b.length, c = b[0].length;

    int[][] res = new int[r][c];

    for (int i = 0; i < r; i++)

        for (int j = 0; j < c; j++)

            for (int k = 0; k < n; k++)

                res[i][j] += a[i][k] * b[k][j];

    return res;

}

```

Time O(r * n * c)

  

### 5.4 Transpose of a Matrix

```java

static int[][] transpose(int[][] a) {

    int[][] t = new int[a[0].length][a.length];

    for (int i = 0; i < a.length; i++)

        for (int j = 0; j < a[0].length; j++)

            t[j][i] = a[i][j];

    return t;

}

```

  

### 5.5 Diagonal Elements Sum

```java

static int diagonalSum(int[][] a) {    // square matrix

    int main = 0, secondary = 0, n = a.length;

    for (int i = 0; i < n; i++) {

        main += a[i][i];

        secondary += a[i][n - 1 - i];

    }

    System.out.println("Secondary diagonal: " + secondary);

    return main;

}

```

  

### 5.6 Upper Triangular Matrix

```java

static void upperTriangular(int[][] a) {

    for (int i = 0; i < a.length; i++) {

        for (int j = 0; j < a[0].length; j++)

            System.out.print((j >= i ? a[i][j] : 0) + " ");

        System.out.println();

    }

}

```

  

### 5.7 Lower Triangular Matrix

```java

static void lowerTriangular(int[][] a) {

    for (int i = 0; i < a.length; i++) {

        for (int j = 0; j < a[0].length; j++)

            System.out.print((j <= i ? a[i][j] : 0) + " ");

        System.out.println();

    }

}

```

  

### 5.8 Check Identity Matrix

```java

static boolean isIdentity(int[][] a) {

    for (int i = 0; i < a.length; i++)

        for (int j = 0; j < a.length; j++)

            if (a[i][j] != (i == j ? 1 : 0)) return false;

    return true;

}

```

  

### 5.9 Check Symmetric Matrix

```java

static boolean isSymmetric(int[][] a) {

    for (int i = 0; i < a.length; i++)

        for (int j = i + 1; j < a.length; j++)

            if (a[i][j] != a[j][i]) return false;

    return true;

}

```

  

### 5.10 Check Sparse Matrix

```java

static boolean isSparse(int[][] a) {     // more than half the elements are zero

    int zeros = 0;

    for (int[] row : a)

        for (int x : row)

            if (x == 0) zeros++;

    return zeros > (a.length * a[0].length) / 2;

}

```

  

---

  

## 6. Arrays: Other Operations

  

### 6.1 Second Largest

```java

static int secondLargest(int[] a) {

    int first = Integer.MIN_VALUE, second = Integer.MIN_VALUE;

    for (int x : a) {

        if (x > first) { second = first; first = x; }

        else if (x > second && x != first) second = x;

    }

    return second;

}

```

One pass, O(n).

  

### 6.2 Second Smallest

```java

static int secondSmallest(int[] a) {

    int first = Integer.MAX_VALUE, second = Integer.MAX_VALUE;

    for (int x : a) {

        if (x < first) { second = first; first = x; }

        else if (x < second && x != first) second = x;

    }

    return second;

}

```

  

### 6.3 Remove Duplicate Elements

```java

static int[] removeDuplicates(int[] a) {

    return Arrays.stream(a).distinct().toArray();

}

```

Keeps original order.

  

### 6.4 Merge Two Arrays

```java

static int[] merge(int[] a, int[] b) {

    int[] res = new int[a.length + b.length];

    System.arraycopy(a, 0, res, 0, a.length);

    System.arraycopy(b, 0, res, a.length, b.length);

    return res;

}

```

  

### 6.5 Split an Array into Two Parts

```java

static void split(int[] a) {

    int mid = a.length / 2;

    int[] first  = Arrays.copyOfRange(a, 0, mid);

    int[] second = Arrays.copyOfRange(a, mid, a.length);

    System.out.println(Arrays.toString(first));

    System.out.println(Arrays.toString(second));

}

```

  

### 6.6 and 6.7 Rotate Left / Right

Reversal method: O(n) time, O(1) space.

```java

static void reverse(int[] a, int i, int j) {

    while (i < j) {

        int t = a[i]; a[i++] = a[j]; a[j--] = t;

    }

}

  

static void rotateRight(int[] a, int k) {

    int n = a.length;

    k %= n;

    reverse(a, 0, n - 1);

    reverse(a, 0, k - 1);

    reverse(a, k, n - 1);

}

  

static void rotateLeft(int[] a, int k) {

    int n = a.length;

    k %= n;

    reverse(a, 0, k - 1);

    reverse(a, k, n - 1);

    reverse(a, 0, n - 1);

}

```

  

### 6.8 Common Elements Between Arrays

```java

static void common(int[] a, int[] b) {

    Set<Integer> set = new HashSet<>();

    for (int x : a) set.add(x);

    Set<Integer> printed = new HashSet<>();

    for (int x : b)

        if (set.contains(x) && printed.add(x))

            System.out.print(x + " ");

}

```

  

### 6.9 Find a Pair with a Given Sum

```java

static void pairSum(int[] a, int target) {

    Set<Integer> seen = new HashSet<>();

    for (int x : a) {

        if (seen.contains(target - x)) {

            System.out.println(x + " + " + (target - x) + " = " + target);

            return;

        }

        seen.add(x);

    }

    System.out.println("No pair found");

}

```

Time O(n), Space O(n)

  

### 6.10 Frequency of Each Element

```java

static void frequency(int[] a) {

    Map<Integer, Integer> map = new LinkedHashMap<>();

    for (int x : a) map.put(x, map.getOrDefault(x, 0) + 1);

    map.forEach((k, v) -> System.out.println(k + " -> " + v));

}

```

  

---

  

## 7. Linked List

  

One class holding every operation. Positions are **1-based**.

  

```java

class Node {

    int data;

    Node next;

    Node(int data) { this.data = data; }

}

  

class MyList {

    Node head;

  

    // 1. Create and display

    void display() {

        for (Node t = head; t != null; t = t.next)

            System.out.print(t.data + " -> ");

        System.out.println("null");

    }

  

    // 2. Insert

    void insertAtBeginning(int val) {

        Node n = new Node(val);

        n.next = head;

        head = n;

    }

  

    void insertAtEnd(int val) {

        Node n = new Node(val);

        if (head == null) { head = n; return; }

        Node t = head;

        while (t.next != null) t = t.next;

        t.next = n;

    }

  

    void insertAtPosition(int pos, int val) {

        if (pos == 1) { insertAtBeginning(val); return; }

        Node t = head;

        for (int i = 1; i < pos - 1 && t != null; i++) t = t.next;

        if (t == null) { System.out.println("Invalid position"); return; }

        Node n = new Node(val);

        n.next = t.next;

        t.next = n;

    }

  

    // 3. Delete

    void deleteAtBeginning() {

        if (head != null) head = head.next;

    }

  

    void deleteAtEnd() {

        if (head == null || head.next == null) { head = null; return; }

        Node t = head;

        while (t.next.next != null) t = t.next;

        t.next = null;

    }

  

    void deleteAtPosition(int pos) {

        if (head == null) return;

        if (pos == 1) { head = head.next; return; }

        Node t = head;

        for (int i = 1; i < pos - 1 && t.next != null; i++) t = t.next;

        if (t.next == null) { System.out.println("Invalid position"); return; }

        t.next = t.next.next;

    }

  

    // 4. Search

    boolean search(int key) {

        for (Node t = head; t != null; t = t.next)

            if (t.data == key) return true;

        return false;

    }

  

    // 5. Count nodes

    int count() {

        int c = 0;

        for (Node t = head; t != null; t = t.next) c++;

        return c;

    }

  

    // 6. Reverse (iterative)

    void reverseIterative() {

        Node prev = null, cur = head;

        while (cur != null) {

            Node next = cur.next;

            cur.next = prev;

            prev = cur;

            cur = next;

        }

        head = prev;

    }

  

    // 7. Reverse (recursive)

    Node reverseRecursive(Node node) {

        if (node == null || node.next == null) return node;

        Node newHead = reverseRecursive(node.next);

        node.next.next = node;

        node.next = null;

        return newHead;

    }

    // usage: head = reverseRecursive(head);

  

    // 8. Middle (slow and fast pointers)

    int middle() {

        Node slow = head, fast = head;

        while (fast != null && fast.next != null) {

            slow = slow.next;

            fast = fast.next.next;

        }

        return slow.data;

    }

  

    // 9. Detect cycle (Floyd)

    boolean hasCycle() {

        Node slow = head, fast = head;

        while (fast != null && fast.next != null) {

            slow = slow.next;

            fast = fast.next.next;

            if (slow == fast) return true;

        }

        return false;

    }

  

    // 10. Remove duplicates (unsorted list)

    void removeDuplicates() {

        Set<Integer> seen = new HashSet<>();

        Node prev = null, cur = head;

        while (cur != null) {

            if (!seen.add(cur.data)) prev.next = cur.next;   // skip duplicate

            else prev = cur;

            cur = cur.next;

        }

    }

  

    // 11. Merge two sorted lists

    static Node mergeSorted(Node a, Node b) {

        Node dummy = new Node(0), tail = dummy;

        while (a != null && b != null) {

            if (a.data <= b.data) { tail.next = a; a = a.next; }

            else                  { tail.next = b; b = b.next; }

            tail = tail.next;

        }

        tail.next = (a != null) ? a : b;

        return dummy.next;

    }

  

    // 12. Check palindrome

    boolean isPalindrome() {

        if (head == null || head.next == null) return true;

  

        Node slow = head, fast = head;                 // find middle

        while (fast.next != null && fast.next.next != null) {

            slow = slow.next;

            fast = fast.next.next;

        }

  

        Node prev = null, cur = slow.next;             // reverse second half

        while (cur != null) {

            Node next = cur.next;

            cur.next = prev;

            prev = cur;

            cur = next;

        }

  

        Node p1 = head, p2 = prev;                     // compare both halves

        while (p2 != null) {

            if (p1.data != p2.data) return false;

            p1 = p1.next;

            p2 = p2.next;

        }

        return true;

    }

}

```

  

| Operation | Time | Space |

|---|---|---|

| Insert at beginning | O(1) | O(1) |

| Insert/Delete at end or position | O(n) | O(1) |

| Search / Count | O(n) | O(1) |

| Reverse | O(n) | O(1) iterative, O(n) recursive |

| Middle / Cycle | O(n) | O(1) |

| Remove duplicates | O(n) | O(n) |

| Merge sorted | O(n + m) | O(1) |

| Palindrome | O(n) | O(1) |

  

---

  

## 8. Practice Problems Q1 to Q10

  

### Q1. Rotate Array (right by k)

```java

static void rotate(int[] a, int k) {

    int n = a.length;

    if (n == 0) return;

    k %= n;

    reverse(a, 0, n - 1);

    reverse(a, 0, k - 1);

    reverse(a, k, n - 1);

}

  

static void reverse(int[] a, int i, int j) {

    while (i < j) {

        int t = a[i]; a[i++] = a[j]; a[j--] = t;

    }

}

```

`[1,2,3,4,5,6,7]`, k=3 gives `[5,6,7,1,2,3,4]`. O(n) time, O(1) space.

  

### Q2. First Unique Character (return index)

```java

static int firstUniqChar(String s) {

    int[] freq = new int[26];

    for (char c : s.toCharArray()) freq[c - 'a']++;

    for (int i = 0; i < s.length(); i++)

        if (freq[s.charAt(i) - 'a'] == 1) return i;

    return -1;

}

```

O(n) time. Assumes lowercase letters.

  

### Q3. Stack with Min

```java

class MinStack {

    private Deque<Integer> stack = new ArrayDeque<>();

    private Deque<Integer> mins  = new ArrayDeque<>();

  

    void push(int x) {

        stack.push(x);

        if (mins.isEmpty() || x <= mins.peek()) mins.push(x);

    }

  

    void pop() {

        if (stack.pop().equals(mins.peek())) mins.pop();

    }

  

    int top()    { return stack.peek(); }

    int getMin() { return mins.peek(); }

}

```

All operations O(1). `equals` is used because `Integer` values must not be compared with `==`.

  

### Q4. Maximum Subarray Sum (Kadane)

```java

static int maxSubarray(int[] a) {

    int cur = a[0], best = a[0];

    for (int i = 1; i < a.length; i++) {

        cur = Math.max(a[i], cur + a[i]);

        best = Math.max(best, cur);

    }

    return best;

}

```

`[-2,1,-3,4,-1,2,1,-5,4]` gives `6`. O(n) time, O(1) space.

  

### Q5. Reverse a String in Place

```java

static void reverseInPlace(char[] s) {

    int i = 0, j = s.length - 1;

    while (i < j) {

        char t = s[i]; s[i++] = s[j]; s[j--] = t;

    }

}

```

O(n) time, O(1) space.

  

### Q6. Check Prime

```java

static boolean isPrime(int n) {

    if (n < 2) return false;

    for (int i = 2; (long) i * i <= n; i++)

        if (n % i == 0) return false;

    return true;

}

```

O(sqrt n). The `long` cast prevents overflow for large n.

  

### Q7. Valid Parentheses

```java

static boolean isValid(String s) {

    Deque<Character> stack = new ArrayDeque<>();

    for (char c : s.toCharArray()) {

        if (c == '(' || c == '[' || c == '{') {

            stack.push(c);

        } else {

            if (stack.isEmpty()) return false;

            char top = stack.pop();

            if ((c == ')' && top != '(') ||

                (c == ']' && top != '[') ||

                (c == '}' && top != '{')) return false;

        }

    }

    return stack.isEmpty();

}

```

O(n) time, O(n) space.

  

### Q8. Two Sum

```java

static int[] twoSum(int[] a, int target) {

    Map<Integer, Integer> map = new HashMap<>();   // value -> index

    for (int i = 0; i < a.length; i++) {

        Integer j = map.get(target - a[i]);

        if (j != null) return new int[]{j, i};

        map.put(a[i], i);

    }

    return new int[]{};

}

```

O(n) time, O(n) space.

  

### Q9. Longest Substring Without Repeating Characters

```java

static int longestUnique(String s) {

    int[] last = new int[256];

    Arrays.fill(last, -1);

    int best = 0, left = 0;

    for (int right = 0; right < s.length(); right++) {

        char c = s.charAt(right);

        if (last[c] >= left) left = last[c] + 1;   // jump past previous occurrence

        last[c] = right;

        best = Math.max(best, right - left + 1);

    }

    return best;

}

```

`"abcabcbb"` gives `3`. O(n) time (sliding window).

  

### Q10. Merge Overlapping Intervals

```java

static int[][] merge(int[][] intervals) {

    if (intervals.length == 0) return new int[0][];

    Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

  

    List<int[]> res = new ArrayList<>();

    int[] cur = intervals[0];

    for (int i = 1; i < intervals.length; i++) {

        if (intervals[i][0] <= cur[1]) {

            cur[1] = Math.max(cur[1], intervals[i][1]);   // overlap, extend

        } else {

            res.add(cur);

            cur = intervals[i];

        }

    }

    res.add(cur);

    return res.toArray(new int[0][]);

}

```

`[[1,3],[2,6],[8,10]]` gives `[[1,6],[8,10]]`. O(n log n) from the sort.

  

### Interview tip (Hexaware)

1. Restate the problem.

2. Say the brute force first, then improve it.

3. Mention edge cases before coding: empty input, single element, overflow.

  

### 2-Week Drill Plan

  

| Day | Drill |

|---|---|

| Mon | Arrays + hashing (2 problems) |

| Tue | Two pointers / sliding window |

| Wed | Stacks / strings |

| Thu | Trees or graphs basics |

| Fri | Timed mock (1-2 problems) |

| Sat | Re-solve misses cold |

| Sun | Explain your project out loud + rest |

  

---

  

## 9. Repeated Items (cross-reference)

  

These appeared twice in your list. One solution each, so no need to learn twice.

  

| Repeated item | Solution |

|---|---|

| Reverse a String | [[#1.1 Reverse a String]] |

| Check Palindrome | [[#1.2 Check Palindrome]] |

| Check Anagram | [[#1.7 Check Anagram]] |

| Count Vowels | [[#1.3 Count Vowels]] |

| Remove Duplicate Characters | [[#1.5 Remove Duplicate Characters]] |

| Find Character Frequency | [[#1.9 Find Character Frequency]] |

| Find Longest Word | [[#1.14 Find Longest Word]] |

| Find First Non-Repeating Character | [[#1.10 Find First Non-Repeating Character]] |

| Largest / Smallest element, Reverse an array | [[#2. Arrays: Basics]] |

| Binary Search / Linear Search | [[#3.2 Binary Search]] / [[#3.1 Linear Search]] |

| Bubble Sort | [[#4.3 Bubble Sort]] |

| Remove duplicates (array) | [[#6.3 Remove Duplicate Elements]] |

| Find missing numbers | [[#3.8 Find a Missing Number]] |

| Rotate arrays | [[#6.6 and 6.7 Rotate Left / Right]] |

| Pair sum problem | [[#6.9 Find a Pair with a Given Sum]] |