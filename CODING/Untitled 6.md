# Java Coding Practice — Complete Code Notes

> [!info] How to use  
> Every program below is standalone. Copy **one program at a time** into `Main.java` and run it. Unless stated otherwise, enter the input in the order shown by the code. Repeated topics in the source checklist are covered by the same core solution rather than duplicated unnecessarily.

> [!warning] Input assumptions  
> The anagram example assumes lowercase `a`–`z`. Binary search requires a sorted array. The missing-number example assumes values from `1` to `n` with one number missing.

## Table of Contents

- [[#strings|Strings]]
- [[#arrays-basics,-search,-and-sorting|Arrays: Basics, Search, and Sorting]]
- [[#matrices|Matrices]]
- [[#arrays-common-interview-problems|Arrays: Common Interview Problems]]
- [[#linked-lists|Linked Lists]]
- [[#hexaware-practice-problems|Hexaware Practice Problems]]

## Strings

### Reverse a String

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine(), res = "";
        for (int i = s.length() - 1; i >= 0; i--) res += s.charAt(i);
        System.out.println(res);
    }
}
```

### Check Palindrome String

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        int left = 0, right = s.length() - 1;
        boolean palindrome = true;
        while (left < right) {
            if (s.charAt(left) != s.charAt(right)) {
                palindrome = false;
                break;
            }
            left++;
            right--;
        }
        System.out.println(palindrome ? "palindrome" : "not palindrome");
    }
}
```

### Count Vowels

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine().toLowerCase();
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') count++;
        }
        System.out.println(count);
    }
}
```

### Count Consonants

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine().toLowerCase();
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (ch >= 'a' && ch <= 'z' &&
                ch != 'a' && ch != 'e' && ch != 'i' && ch != 'o' && ch != 'u') count++;
        }
        System.out.println(count);
    }
}
```

### Remove Duplicate Characters

> [!tip] Note  
> Keeps the first occurrence of each character.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine(), res = "";
        for (int i = 0; i < s.length(); i++) {
            boolean found = false;
            for (int j = 0; j < i; j++) {
                if (s.charAt(i) == s.charAt(j)) {
                    found = true;
                    break;
                }
            }
            if (!found) res += s.charAt(i);
        }
        System.out.println(res);
    }
}
```

### Find Duplicate Characters

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        LinkedHashMap<Character, Integer> map = new LinkedHashMap<>();
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }
        for (char ch : map.keySet()) {
            if (map.get(ch) > 1) System.out.println(ch);
        }
    }
}
```

### Check Anagram (lowercase a-z)

> [!tip] Note  
> Assumes lowercase English letters and no spaces.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.nextLine(), b = sc.nextLine();
        if (a.length() != b.length()) {
            System.out.println("Not Anagram");
            return;
        }
        int[] count = new int[26];
        for (int i = 0; i < a.length(); i++) {
            count[a.charAt(i) - 'a']++;
            count[b.charAt(i) - 'a']--;
        }
        for (int n : count) {
            if (n != 0) {
                System.out.println("Not Anagram");
                return;
            }
        }
        System.out.println("Anagram");
    }
}
```

### Count Words

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine().trim();
        if (s.isEmpty()) System.out.println(0);
        else System.out.println(s.split("\\s+").length);
    }
}
```

### Find Character Frequency

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        char target = sc.next().charAt(0);
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == target) count++;
        }
        System.out.println(count);
    }
}
```

### Find First Non-Repeating Character

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        LinkedHashMap<Character, Integer> map = new LinkedHashMap<>();
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }
        for (int i = 0; i < s.length(); i++) {
            if (map.get(s.charAt(i)) == 1) {
                System.out.println(s.charAt(i));
                return;
            }
        }
        System.out.println("No non-repeating character");
    }
}
```

### Replace Characters (without replace())

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        char oldChar = sc.next().charAt(0);
        char newChar = sc.next().charAt(0);
        String result = "";
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == oldChar) result += newChar;
            else result += s.charAt(i);
        }
        System.out.println(result);
    }
}
```

### Remove Spaces

> [!tip] Note  
> Removes ordinary space characters.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine(), result = "";
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) != ' ') result += s.charAt(i);
        }
        System.out.println(result);
    }
}
```

### Sort Characters

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        char[] a = sc.nextLine().toCharArray();
        Arrays.sort(a);
        System.out.println(new String(a));
    }
}
```

### Find Longest Word

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine().trim();
        if (s.isEmpty()) {
            System.out.println("");
            return;
        }
        String[] words = s.split("\\s+");
        String longest = words[0];
        for (String word : words) {
            if (word.length() > longest.length()) longest = word;
        }
        System.out.println(longest);
    }
}
```

### Extract Numbers from a String

> [!tip] Note  
> Prints each consecutive group of digits on a separate line.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        String number = "";
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (ch >= '0' && ch <= '9') number += ch;
            else if (!number.isEmpty()) {
                System.out.println(number);
                number = "";
            }
        }
        if (!number.isEmpty()) System.out.println(number);
    }
}
```

### Reverse Words in a Sentence

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine().trim();
        if (s.isEmpty()) {
            System.out.println("");
            return;
        }
        String[] words = s.split("\\s+");
        for (int i = words.length - 1; i >= 0; i--) {
            System.out.print(words[i]);
            if (i > 0) System.out.print(" ");
        }
    }
}
```

### String Compression (e.g. aaabbc -> a3b2c1)

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine(), result = "";
        int i = 0;
        while (i < s.length()) {
            char ch = s.charAt(i);
            int count = 0;
            while (i < s.length() && s.charAt(i) == ch) {
                count++;
                i++;
            }
            result += ch + String.valueOf(count);
        }
        System.out.println(result);
    }
}
```

## Arrays: Basics, Search, and Sorting

### Read and Display Array Elements

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        for (int x : a) System.out.print(x + " ");
    }
}
```

### Sum of Array Elements

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        long sum = 0;
        for (int i = 0; i < n; i++) { a[i] = sc.nextInt(); sum += a[i]; }
        System.out.println(sum);
    }
}
```

### Average of Array Elements

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        long sum = 0;
        for (int i = 0; i < n; i++) { a[i] = sc.nextInt(); sum += a[i]; }
        System.out.println(n == 0 ? 0 : (double) sum / n);
    }
}
```

### Largest Element

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        if (n == 0) return;
        int max = sc.nextInt();
        for (int i = 1; i < n; i++) max = Math.max(max, sc.nextInt());
        System.out.println(max);
    }
}
```

### Smallest Element

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        if (n == 0) return;
        int min = sc.nextInt();
        for (int i = 1; i < n; i++) min = Math.min(min, sc.nextInt());
        System.out.println(min);
    }
}
```

### Count Array Elements

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        System.out.println(a.length);
    }
}
```

### Display Array in Reverse Order

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        for (int i = n - 1; i >= 0; i--) System.out.print(a[i] + " ");
    }
}
```

### Copy One Array into Another

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n], b = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        for (int i = 0; i < n; i++) b[i] = a[i];
        System.out.println(Arrays.toString(b));
    }
}
```

### Print Even Elements

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        for (int i = 0; i < n; i++) { int x = sc.nextInt(); if (x % 2 == 0) System.out.print(x + " "); }
    }
}
```

### Print Odd Elements

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        for (int i = 0; i < n; i++) { int x = sc.nextInt(); if (x % 2 != 0) System.out.print(x + " "); }
    }
}
```

### Linear Search

> [!tip] Note  
> Prints the first matching index, or -1.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(), target;
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        target = sc.nextInt();
        for (int i = 0; i < n; i++) if (a[i] == target) { System.out.println(i); return; }
        System.out.println(-1);
    }
}
```

### Binary Search (sorted array)

> [!tip] Note  
> Input array must be sorted in ascending order.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        int target = sc.nextInt(), left = 0, right = n - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (a[mid] == target) { System.out.println(mid); return; }
            if (a[mid] < target) left = mid + 1;
            else right = mid - 1;
        }
        System.out.println(-1);
    }
}
```

### Search an Element Using User Input

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        System.out.print("Enter target: ");
        int target = sc.nextInt();
        boolean found = false;
        for (int x : a) if (x == target) { found = true; break; }
        System.out.println(found ? "Found" : "Not found");
    }
}
```

### Count Occurrences of an Element

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(), count = 0;
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        int target = sc.nextInt();
        for (int x : a) if (x == target) count++;
        System.out.println(count);
    }
}
```

### First Occurrence of an Element

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        int target = sc.nextInt();
        for (int i = 0; i < n; i++) if (a[i] == target) { System.out.println(i); return; }
        System.out.println(-1);
    }
}
```

### Last Occurrence of an Element

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        int target = sc.nextInt();
        for (int i = n - 1; i >= 0; i--) if (a[i] == target) { System.out.println(i); return; }
        System.out.println(-1);
    }
}
```

### Search Multiple Elements

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        int q = sc.nextInt();
        while (q-- > 0) {
            int target = sc.nextInt();
            boolean found = false;
            for (int x : a) if (x == target) { found = true; break; }
            System.out.println(found ? "Found" : "Not found");
        }
    }
}
```

### Find a Missing Number (1 to n)

> [!tip] Note  
> Input contains n-1 distinct values from 1 through n.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        long expected = (long) n * (n + 1) / 2, sum = 0;
        for (int i = 0; i < n - 1; i++) sum += sc.nextInt();
        System.out.println(expected - sum);
    }
}
```

### Check Whether an Element Exists

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        int target = sc.nextInt();
        boolean exists = false;
        for (int x : a) if (x == target) { exists = true; break; }
        System.out.println(exists);
    }
}
```

### Find Duplicate Elements

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        LinkedHashSet<Integer> seen = new LinkedHashSet<>(), duplicates = new LinkedHashSet<>();
        for (int x : a) if (!seen.add(x)) duplicates.add(x);
        System.out.println(duplicates);
    }
}
```

### Sort Array Ascending (manual)

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        for (int i = 0; i < n - 1; i++)
            for (int j = i + 1; j < n; j++)
                if (a[i] > a[j]) { int t = a[i]; a[i] = a[j]; a[j] = t; }
        System.out.println(Arrays.toString(a));
    }
}
```

### Sort Array Descending (manual)

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        for (int i = 0; i < n - 1; i++)
            for (int j = i + 1; j < n; j++)
                if (a[i] < a[j]) { int t = a[i]; a[i] = a[j]; a[j] = t; }
        System.out.println(Arrays.toString(a));
    }
}
```

### Bubble Sort

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        for (int i = 0; i < n - 1; i++)
            for (int j = 0; j < n - 1 - i; j++)
                if (a[j] > a[j + 1]) { int t = a[j]; a[j] = a[j + 1]; a[j + 1] = t; }
        System.out.println(Arrays.toString(a));
    }
}
```

### Selection Sort

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        for (int i = 0; i < n - 1; i++) {
            int min = i;
            for (int j = i + 1; j < n; j++) if (a[j] < a[min]) min = j;
            int t = a[i]; a[i] = a[min]; a[min] = t;
        }
        System.out.println(Arrays.toString(a));
    }
}
```

### Insertion Sort

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        for (int i = 1; i < n; i++) {
            int key = a[i], j = i - 1;
            while (j >= 0 && a[j] > key) { a[j + 1] = a[j]; j--; }
            a[j + 1] = key;
        }
        System.out.println(Arrays.toString(a));
    }
}
```

### Sort String Array Alphabetically

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = Integer.parseInt(sc.nextLine());
        String[] a = new String[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextLine();
        Arrays.sort(a, String.CASE_INSENSITIVE_ORDER);
        for (String s : a) System.out.println(s);
    }
}
```

### Sort Using Arrays.sort()

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        Arrays.sort(a);
        System.out.println(Arrays.toString(a));
    }
}
```

### Sort Only Even Numbers (even positions' values sorted)

> [!tip] Note  
> Sorts even-valued elements while odd-valued elements stay in their original positions.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        ArrayList<Integer> even = new ArrayList<>();
        for (int x : a) if (x % 2 == 0) even.add(x);
        Collections.sort(even);
        int k = 0;
        for (int i = 0; i < n; i++) if (a[i] % 2 == 0) a[i] = even.get(k++);
        System.out.println(Arrays.toString(a));
    }
}
```

### Sort Only Odd Numbers (odd positions' values sorted)

> [!tip] Note  
> Sorts odd-valued elements while even-valued elements stay in their original positions.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        ArrayList<Integer> odd = new ArrayList<>();
        for (int x : a) if (x % 2 != 0) odd.add(x);
        Collections.sort(odd);
        int k = 0;
        for (int i = 0; i < n; i++) if (a[i] % 2 != 0) a[i] = odd.get(k++);
        System.out.println(Arrays.toString(a));
    }
}
```

### Sort Without Built-in Functions

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];
        for (int i = 0; i < n; i++) a[i] = sc.nextInt();
        for (int i = 0; i < n - 1; i++)
            for (int j = 0; j < n - 1 - i; j++)
                if (a[j] > a[j + 1]) { int t = a[j]; a[j] = a[j + 1]; a[j + 1] = t; }
        System.out.println(Arrays.toString(a));
    }
}
```

## Matrices

### Add Two Matrices

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int r = sc.nextInt(), c = sc.nextInt();
        int[][] a = new int[r][c], b = new int[r][c];
        for (int i=0;i<r;i++) for (int j=0;j<c;j++) a[i][j]=sc.nextInt();
        for (int i=0;i<r;i++) for (int j=0;j<c;j++) b[i][j]=sc.nextInt();
        for (int i=0;i<r;i++) {
            for (int j=0;j<c;j++) System.out.print((a[i][j]+b[i][j])+" ");
            System.out.println();
        }
    }
}
```

### Subtract Two Matrices

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int r = sc.nextInt(), c = sc.nextInt();
        int[][] a = new int[r][c], b = new int[r][c];
        for (int i=0;i<r;i++) for (int j=0;j<c;j++) a[i][j]=sc.nextInt();
        for (int i=0;i<r;i++) for (int j=0;j<c;j++) b[i][j]=sc.nextInt();
        for (int i=0;i<r;i++) {
            for (int j=0;j<c;j++) System.out.print((a[i][j]-b[i][j])+" ");
            System.out.println();
        }
    }
}
```

### Multiply Two Matrices

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int r1=sc.nextInt(), c1=sc.nextInt();
        int[][] a=new int[r1][c1];
        for(int i=0;i<r1;i++) for(int j=0;j<c1;j++) a[i][j]=sc.nextInt();
        int r2=sc.nextInt(), c2=sc.nextInt();
        int[][] b=new int[r2][c2];
        for(int i=0;i<r2;i++) for(int j=0;j<c2;j++) b[i][j]=sc.nextInt();
        if(c1!=r2) { System.out.println("Multiplication not possible"); return; }
        int[][] res=new int[r1][c2];
        for(int i=0;i<r1;i++) for(int j=0;j<c2;j++)
            for(int k=0;k<c1;k++) res[i][j]+=a[i][k]*b[k][j];
        for(int[] row:res) { for(int x:row) System.out.print(x+" "); System.out.println(); }
    }
}
```

### Transpose of a Matrix

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int r=sc.nextInt(), c=sc.nextInt();
        int[][] a=new int[r][c];
        for(int i=0;i<r;i++) for(int j=0;j<c;j++) a[i][j]=sc.nextInt();
        for(int j=0;j<c;j++) {
            for(int i=0;i<r;i++) System.out.print(a[i][j]+" ");
            System.out.println();
        }
    }
}
```

### Sum of Main Diagonal Elements

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(), sum=0;
        int[][] a=new int[n][n];
        for(int i=0;i<n;i++) for(int j=0;j<n;j++) a[i][j]=sc.nextInt();
        for(int i=0;i<n;i++) sum+=a[i][i];
        System.out.println(sum);
    }
}
```

### Upper Triangular Matrix

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        int[][] a=new int[n][n];
        for(int i=0;i<n;i++) for(int j=0;j<n;j++) a[i][j]=sc.nextInt();
        for(int i=0;i<n;i++) {
            for(int j=0;j<n;j++) System.out.print((i<=j?a[i][j]:0)+" ");
            System.out.println();
        }
    }
}
```

### Lower Triangular Matrix

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        int[][] a=new int[n][n];
        for(int i=0;i<n;i++) for(int j=0;j<n;j++) a[i][j]=sc.nextInt();
        for(int i=0;i<n;i++) {
            for(int j=0;j<n;j++) System.out.print((i>=j?a[i][j]:0)+" ");
            System.out.println();
        }
    }
}
```

### Check Identity Matrix

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        boolean identity=true;
        for(int i=0;i<n;i++) for(int j=0;j<n;j++) {
            int x=sc.nextInt();
            if((i==j && x!=1)||(i!=j && x!=0)) identity=false;
        }
        System.out.println(identity?"Identity matrix":"Not identity matrix");
    }
}
```

### Check Symmetric Matrix

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        int[][] a=new int[n][n];
        for(int i=0;i<n;i++) for(int j=0;j<n;j++) a[i][j]=sc.nextInt();
        boolean symmetric=true;
        for(int i=0;i<n;i++) for(int j=0;j<n;j++) if(a[i][j]!=a[j][i]) symmetric=false;
        System.out.println(symmetric?"Symmetric":"Not symmetric");
    }
}
```

### Check Sparse Matrix (zeros are more than non-zeros)

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int r=sc.nextInt(), c=sc.nextInt(), zeros=0;
        for(int i=0;i<r;i++) for(int j=0;j<c;j++) if(sc.nextInt()==0) zeros++;
        System.out.println(zeros > (r*c)/2 ? "Sparse matrix" : "Not sparse matrix");
    }
}
```

## Arrays: Common Interview Problems

### Second Largest Distinct Element

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        int[] a=new int[n];
        for(int i=0;i<n;i++) a[i]=sc.nextInt();
        Integer largest=null, second=null;
        for(int x:a) {
            if(largest==null || x>largest) { if(largest!=null) second=largest; largest=x; }
            else if(x!=largest && (second==null || x>second)) second=x;
        }
        System.out.println(second==null?"No second largest":second);
    }
}
```

### Second Smallest Distinct Element

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        Integer smallest=null, second=null;
        for(int i=0;i<n;i++) {
            int x=sc.nextInt();
            if(smallest==null || x<smallest) { if(smallest!=null) second=smallest; smallest=x; }
            else if(x!=smallest && (second==null || x<second)) second=x;
        }
        System.out.println(second==null?"No second smallest":second);
    }
}
```

### Remove Duplicate Array Elements

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        LinkedHashSet<Integer> set=new LinkedHashSet<>();
        for(int i=0;i<n;i++) set.add(sc.nextInt());
        System.out.println(set);
    }
}
```

### Merge Two Arrays

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(); int[] a=new int[n];
        for(int i=0;i<n;i++) a[i]=sc.nextInt();
        int m=sc.nextInt(); int[] b=new int[m];
        for(int i=0;i<m;i++) b[i]=sc.nextInt();
        int[] c=new int[n+m];
        for(int i=0;i<n;i++) c[i]=a[i];
        for(int i=0;i<m;i++) c[n+i]=b[i];
        System.out.println(Arrays.toString(c));
    }
}
```

### Split Array into Two Parts

> [!tip] Note  
> Input: n, split index k, then n array elements.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(), k=sc.nextInt();
        int[] a=new int[n];
        for(int i=0;i<n;i++) a[i]=sc.nextInt();
        k=Math.max(0,Math.min(k,n));
        System.out.println("First: "+Arrays.toString(Arrays.copyOfRange(a,0,k)));
        System.out.println("Second: "+Arrays.toString(Arrays.copyOfRange(a,k,n)));
    }
}
```

### Rotate Array Left by k

```
import java.util.*;
public class Main {
    static void reverse(int[] a,int l,int r) {
        while(l<r) { int t=a[l]; a[l]=a[r]; a[r]=t; l++; r--; }
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(); int[] a=new int[n];
        for(int i=0;i<n;i++) a[i]=sc.nextInt();
        int k=sc.nextInt();
        if(n>0) { k=((k%n)+n)%n; reverse(a,0,k-1); reverse(a,k,n-1); reverse(a,0,n-1); }
        System.out.println(Arrays.toString(a));
    }
}
```

### Rotate Array Right by k

```
import java.util.*;
public class Main {
    static void reverse(int[] a,int l,int r) {
        while(l<r) { int t=a[l]; a[l]=a[r]; a[r]=t; l++; r--; }
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(); int[] a=new int[n];
        for(int i=0;i<n;i++) a[i]=sc.nextInt();
        int k=sc.nextInt();
        if(n>0) { k=((k%n)+n)%n; reverse(a,0,n-1); reverse(a,0,k-1); reverse(a,k,n-1); }
        System.out.println(Arrays.toString(a));
    }
}
```

### Common Elements Between Two Arrays

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(); Set<Integer> a=new HashSet<>();
        for(int i=0;i<n;i++) a.add(sc.nextInt());
        int m=sc.nextInt(); Set<Integer> common=new LinkedHashSet<>();
        for(int i=0;i<m;i++) { int x=sc.nextInt(); if(a.contains(x)) common.add(x); }
        System.out.println(common);
    }
}
```

### Pair with Given Sum (print indices)

> [!tip] Note  
> Brute-force approach; prints the first pair of indices.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(); int[] a=new int[n];
        for(int i=0;i<n;i++) a[i]=sc.nextInt();
        int target=sc.nextInt();
        for(int i=0;i<n;i++) for(int j=i+1;j<n;j++)
            if(a[i]+a[j]==target) { System.out.println(i+" "+j); return; }
        System.out.println(-1);
    }
}
```

### Frequency of Each Array Element

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt();
        Map<Integer,Integer> map=new LinkedHashMap<>();
        for(int i=0;i<n;i++) { int x=sc.nextInt(); map.put(x,map.getOrDefault(x,0)+1); }
        for(int x:map.keySet()) System.out.println(x+" : "+map.get(x));
    }
}
```

### Find All Missing Numbers from 1 to n

> [!tip] Note  
> Input has n values in the range 1..n; repeated values can cause missing values.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(); boolean[] seen=new boolean[n+1];
        for(int i=0;i<n;i++) { int x=sc.nextInt(); if(x>=1 && x<=n) seen[x]=true; }
        for(int i=1;i<=n;i++) if(!seen[i]) System.out.print(i+" ");
    }
}
```

## Linked Lists

### Create and Display a Linked List

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int data){this.data=data;} }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(); Node head=null, tail=null;
        for(int i=0;i<n;i++) {
            Node node=new Node(sc.nextInt());
            if(head==null) head=node; else tail.next=node;
            tail=node;
        }
        for(Node cur=head;cur!=null;cur=cur.next) System.out.print(cur.data+" ");
    }
}
```

### Insert Node at Beginning, End, and Position

> [!tip] Note  
> Position is zero-based; position 0 inserts at the beginning.

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int d){data=d;} }
    static Node insertEnd(Node h,int x) {
        Node n=new Node(x); if(h==null)return n;
        Node c=h; while(c.next!=null)c=c.next; c.next=n; return h;
    }
    static Node insertAt(Node h,int x,int pos) {
        Node n=new Node(x);
        if(pos<=0 || h==null) { n.next=h; return n; }
        Node c=h;
        for(int i=0;i<pos-1 && c.next!=null;i++) c=c.next;
        n.next=c.next; c.next=n; return h;
    }
    static void print(Node h){for(Node c=h;c!=null;c=c.next)System.out.print(c.data+" ");}
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); int n=sc.nextInt(); Node h=null;
        for(int i=0;i<n;i++)h=insertEnd(h,sc.nextInt());
        int value=sc.nextInt(), position=sc.nextInt();
        h=insertAt(h,value,position); print(h);
    }
}
```

### Delete Node at Beginning, End, or Position

> [!tip] Note  
> Position is zero-based; use position 0 to delete the first node.

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int d){data=d;} }
    static Node deleteAt(Node h,int pos) {
        if(h==null)return null;
        if(pos<=0)return h.next;
        Node c=h;
        for(int i=0;i<pos-1 && c.next!=null;i++)c=c.next;
        if(c.next!=null)c.next=c.next.next;
        return h;
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); int n=sc.nextInt(); Node h=null,tail=null;
        for(int i=0;i<n;i++){Node x=new Node(sc.nextInt());if(h==null)h=x;else tail.next=x;tail=x;}
        int pos=sc.nextInt(); h=deleteAt(h,pos);
        for(Node c=h;c!=null;c=c.next)System.out.print(c.data+" ");
    }
}
```

### Search an Element in a Linked List

> [!tip] Note  
> Prints index of first match, or -1.

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int d){data=d;} }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); int n=sc.nextInt(); Node h=null,tail=null;
        for(int i=0;i<n;i++){Node x=new Node(sc.nextInt());if(h==null)h=x;else tail.next=x;tail=x;}
        int target=sc.nextInt(), index=0;
        for(Node c=h;c!=null;c=c.next,index++)if(c.data==target){System.out.println(index);return;}
        System.out.println(-1);
    }
}
```

### Count Nodes in a Linked List

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int d){data=d;} }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); int n=sc.nextInt(); Node h=null,tail=null;
        for(int i=0;i<n;i++){Node x=new Node(sc.nextInt());if(h==null)h=x;else tail.next=x;tail=x;}
        int count=0; for(Node c=h;c!=null;c=c.next)count++;
        System.out.println(count);
    }
}
```

### Reverse Linked List (Iterative)

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int d){data=d;} }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); int n=sc.nextInt(); Node h=null,tail=null;
        for(int i=0;i<n;i++){Node x=new Node(sc.nextInt());if(h==null)h=x;else tail.next=x;tail=x;}
        Node prev=null,cur=h;
        while(cur!=null){Node next=cur.next;cur.next=prev;prev=cur;cur=next;}
        for(Node c=prev;c!=null;c=c.next)System.out.print(c.data+" ");
    }
}
```

### Reverse Linked List (Recursive)

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int d){data=d;} }
    static Node reverse(Node h) {
        if(h==null || h.next==null)return h;
        Node newHead=reverse(h.next);
        h.next.next=h; h.next=null;
        return newHead;
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); int n=sc.nextInt(); Node h=null,tail=null;
        for(int i=0;i<n;i++){Node x=new Node(sc.nextInt());if(h==null)h=x;else tail.next=x;tail=x;}
        h=reverse(h);
        for(Node c=h;c!=null;c=c.next)System.out.print(c.data+" ");
    }
}
```

### Find Middle of a Linked List

> [!tip] Note  
> For an even-length list, returns the second middle node.

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int d){data=d;} }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); int n=sc.nextInt(); Node h=null,tail=null;
        for(int i=0;i<n;i++){Node x=new Node(sc.nextInt());if(h==null)h=x;else tail.next=x;tail=x;}
        Node slow=h,fast=h;
        while(fast!=null && fast.next!=null){slow=slow.next;fast=fast.next.next;}
        if(slow!=null)System.out.println(slow.data);
    }
}
```

### Detect Cycle in a Linked List (Floyd's Algorithm)

> [!tip] Note  
> Demonstration creates an acyclic list. Uncomment c.next=b to test a cycle.

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int d){data=d;} }
    static boolean hasCycle(Node h) {
        Node slow=h,fast=h;
        while(fast!=null && fast.next!=null) {
            slow=slow.next; fast=fast.next.next;
            if(slow==fast)return true;
        }
        return false;
    }
    public static void main(String[] args) {
        Node a=new Node(1),b=new Node(2),c=new Node(3);
        a.next=b; b.next=c;
        // Uncomment the next line to create a cycle: c.next = b;
        System.out.println(hasCycle(a));
    }
}
```

### Remove Duplicates from a Linked List

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int d){data=d;} }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); int n=sc.nextInt(); Node h=null,tail=null;
        for(int i=0;i<n;i++){Node x=new Node(sc.nextInt());if(h==null)h=x;else tail.next=x;tail=x;}
        Set<Integer> seen=new HashSet<>(); Node cur=h,prev=null;
        while(cur!=null){
            if(seen.contains(cur.data))prev.next=cur.next;
            else {seen.add(cur.data);prev=cur;}
            cur=cur.next;
        }
        for(Node c=h;c!=null;c=c.next)System.out.print(c.data+" ");
    }
}
```

### Merge Two Sorted Linked Lists

> [!tip] Note  
> Input: n1, n1 sorted values, n2, n2 sorted values.

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int d){data=d;} }
    static Node append(Node tail,int x){tail.next=new Node(x);return tail.next;}
    static Node merge(Node a,Node b) {
        Node dummy=new Node(0),tail=dummy;
        while(a!=null && b!=null) {
            if(a.data<=b.data){tail.next=a;a=a.next;}
            else {tail.next=b;b=b.next;}
            tail=tail.next;
        }
        tail.next=(a!=null)?a:b;
        return dummy.next;
    }
    static Node read(Scanner sc,int n) {
        Node h=null,t=null;
        for(int i=0;i<n;i++){Node x=new Node(sc.nextInt());if(h==null)h=x;else t.next=x;t=x;}
        return h;
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        Node a=read(sc,sc.nextInt()), b=read(sc,sc.nextInt());
        for(Node c=merge(a,b);c!=null;c=c.next)System.out.print(c.data+" ");
    }
}
```

### Check Whether Linked List Is Palindrome

> [!tip] Note  
> Stores input values in an array to make the palindrome check simple.

```
import java.util.*;
public class Main {
    static class Node { int data; Node next; Node(int d){data=d;} }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); int n=sc.nextInt(); int[] a=new int[n];
        for(int i=0;i<n;i++)a[i]=sc.nextInt();
        boolean ok=true;
        for(int i=0;i<n/2;i++)if(a[i]!=a[n-1-i]){ok=false;break;}
        System.out.println(ok?"Palindrome":"Not palindrome");
    }
}
```

## Hexaware Practice Problems

### Q1. Rotate Array Right by k (in-place)

> [!tip] Note  
> Input: n, n elements, k. O(n) time, O(1) extra space.

```
import java.util.*;
public class Main {
    static void reverse(int[] a,int l,int r) {
        while(l<r){int t=a[l];a[l]=a[r];a[r]=t;l++;r--;}
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(); int[] a=new int[n];
        for(int i=0;i<n;i++)a[i]=sc.nextInt();
        int k=sc.nextInt();
        if(n>0){k=((k%n)+n)%n;reverse(a,0,n-1);reverse(a,0,k-1);reverse(a,k,n-1);}
        System.out.println(Arrays.toString(a));
    }
}
```

### Q2. First Unique Character Index

> [!tip] Note  
> O(n) time; prints the index, not the character.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); String s=sc.nextLine();
        int[] count=new int[65536];
        for(int i=0;i<s.length();i++)count[s.charAt(i)]++;
        for(int i=0;i<s.length();i++)if(count[s.charAt(i)]==1){System.out.println(i);return;}
        System.out.println(-1);
    }
}
```

### Q3. Stack with getMin

> [!tip] Note  
> Each command is entered on its own line or separated by spaces. Avoid pop/top/getMin on an empty stack.

```
import java.util.*;
public class Main {
    static class MinStack {
        Stack<Integer> values=new Stack<>(), mins=new Stack<>();
        void push(int x){values.push(x);if(mins.empty()||x<=mins.peek())mins.push(x);}
        int pop(){int x=values.pop();if(x==mins.peek())mins.pop();return x;}
        int top(){return values.peek();}
        int getMin(){return mins.peek();}
        boolean isEmpty(){return values.empty();}
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); MinStack s=new MinStack();
        // Commands: push x | pop | top | getMin | end
        while(sc.hasNext()) {
            String cmd=sc.next();
            if(cmd.equals("end"))break;
            if(cmd.equals("push"))s.push(sc.nextInt());
            else if(cmd.equals("pop")){if(!s.isEmpty())System.out.println(s.pop());}
            else if(cmd.equals("top")){if(!s.isEmpty())System.out.println(s.top());}
            else if(cmd.equals("getMin")){if(!s.isEmpty())System.out.println(s.getMin());}
        }
    }
}
```

### Q4. Maximum Subarray Sum (Kadane)

> [!tip] Note  
> Handles all-negative arrays. O(n) time, O(1) space.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(); if(n==0){System.out.println(0);return;}
        int current=sc.nextInt(), best=current;
        for(int i=1;i<n;i++){
            int x=sc.nextInt();
            current=Math.max(x,current+x);
            best=Math.max(best,current);
        }
        System.out.println(best);
    }
}
```

### Q5. Reverse Character Array In Place

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        char[] a=sc.nextLine().toCharArray();
        int l=0,r=a.length-1;
        while(l<r){char t=a[l];a[l]=a[r];a[r]=t;l++;r--;}
        System.out.println(new String(a));
    }
}
```

### Q6. Check Prime

> [!tip] Note  
> Checks divisors up to square root; avoids i*i overflow.

```
import java.util.*;
public class Main {
    static boolean isPrime(int n) {
        if(n<2)return false;
        for(int i=2;i<=n/i;i++)if(n%i==0)return false;
        return true;
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        System.out.println(isPrime(sc.nextInt()));
    }
}
```

### Q7. Valid Parentheses () [] {}

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); String s=sc.nextLine();
        Stack<Character> st=new Stack<>();
        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);
            if(ch=='('||ch=='['||ch=='{')st.push(ch);
            else if(ch==')'||ch==']'||ch=='}'){
                if(st.empty()){System.out.println(false);return;}
                char open=st.pop();
                if((ch==')'&&open!='(')||(ch==']'&&open!='[')||(ch=='}'&&open!='{')){
                    System.out.println(false);return;
                }
            }
        }
        System.out.println(st.empty());
    }
}
```

### Q8. Two Sum (return indices)

> [!tip] Note  
> Input: n, array elements, target. Indices are zero-based.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(); int[] a=new int[n];
        for(int i=0;i<n;i++)a[i]=sc.nextInt();
        int target=sc.nextInt(); Map<Integer,Integer> map=new HashMap<>();
        for(int i=0;i<n;i++){
            int need=target-a[i];
            if(map.containsKey(need)){System.out.println(map.get(need)+" "+i);return;}
            map.put(a[i],i);
        }
        System.out.println("-1 -1");
    }
}
```

### Q9. Longest Substring Without Repeating Characters

> [!tip] Note  
> Sliding window; O(n) time.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in); String s=sc.nextLine();
        Map<Character,Integer> last=new HashMap<>();
        int left=0,best=0;
        for(int right=0;right<s.length();right++){
            char ch=s.charAt(right);
            if(last.containsKey(ch))left=Math.max(left,last.get(ch)+1);
            last.put(ch,right);
            best=Math.max(best,right-left+1);
        }
        System.out.println(best);
    }
}
```

### Q10. Merge Overlapping Intervals

> [!tip] Note  
> Input: n, then n start/end pairs. O(n log n) time.

```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        int n=sc.nextInt(); int[][] a=new int[n][2];
        for(int i=0;i<n;i++){a[i][0]=sc.nextInt();a[i][1]=sc.nextInt();}
        Arrays.sort(a,(x,y)->Integer.compare(x[0],y[0]));
        List<int[]> res=new ArrayList<>();
        for(int[] in:a){
            if(res.isEmpty()||res.get(res.size()-1)[1]<in[0])res.add(new int[]{in[0],in[1]});
            else res.get(res.size()-1)[1]=Math.max(res.get(res.size()-1)[1],in[1]);
        }
        for(int[] in:res)System.out.println(in[0]+" "+in[1]);
    }
}
```

## Checklist coverage

### Strings

- [ ] Reverse a string
- [ ] Check palindrome
- [ ] Count vowels
- [ ] Count consonants
- [ ] Remove duplicate characters
- [ ] Find duplicate characters
- [ ] Check anagram
- [ ] Count words
- [ ] Find character frequency
- [ ] Find first non-repeating character
- [ ] Replace characters without `replace()`
- [ ] Remove spaces
- [ ] Sort characters
- [ ] Find longest word
- [ ] Extract numbers from a string
- [ ] Reverse words in a sentence
- [ ] String compression

### Arrays

- [ ] Read/display, sum, average, largest, smallest, length
- [ ] Reverse display, copy array, print even/odd values
- [ ] Linear search and binary search
- [ ] Search target, count occurrences, first/last occurrence
- [ ] Search multiple targets, missing number, existence check
- [ ] Find duplicates
- [ ] Ascending/descending sorting
- [ ] Bubble, selection, insertion sort
- [ ] Sort string arrays; `Arrays.sort()`
- [ ] Sort only even/odd values; sort without built-ins
- [ ] Second largest and second smallest distinct values
- [ ] Remove duplicates, merge arrays, split array
- [ ] Rotate left/right, common elements, pair sum, frequency
- [ ] Find all missing numbers

### Matrices

- [ ] Add and subtract matrices
- [ ] Multiply matrices
- [ ] Transpose
- [ ] Main diagonal sum
- [ ] Upper/lower triangular matrices
- [ ] Identity, symmetric, sparse matrix checks

### Linked Lists

- [ ] Create/display
- [ ] Insert at position
- [ ] Delete at position (position 0 deletes the beginning; deleting the end uses the last index)
- [ ] Search
- [ ] Count nodes
- [ ] Reverse iterative and recursive
- [ ] Find middle
- [ ] Detect cycle
- [ ] Remove duplicates
- [ ] Merge sorted lists
- [ ] Check palindrome

### Interview practice

- [ ] Rotate array right by k
- [ ] First unique character index
- [ ] Stack with minimum
- [ ] Maximum subarray sum (Kadane)
- [ ] Reverse character array in place
- [ ] Prime check
- [ ] Valid parentheses
- [ ] Two Sum
- [ ] Longest substring without repeating characters
- [ ] Merge overlapping intervals

## Study rule

Mark a checkbox only after you can write the solution yourself without looking at the code. For coding assessments, practise explaining the approach and time/space complexity after solving.