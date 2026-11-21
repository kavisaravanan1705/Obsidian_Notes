**Problem 1:**

**Adam's Charity**

Adam decides to be generous and do some charity. Starting today, from day 1 until day n, he gives i^2 coins to charity on day ‘i’ (1≤i≤n).

Return the total coins, he would give to charity.

**Input specification:**

**Input 1:** number of days of Charity.

**Output Specification:**

Return the total number of coins till charity days.

**Example 1:**

**Input 1:** 2

**Output:** 5

**Explanation:**

There are 2 days.

**Example 2:**

**Input 1:** 3

**Output:** 14

**Explanation:**

There are 3 days.

**Code:**

import java.util.*;

class Main

{

  public static void main(String args[])

  {

    Scanner scan = new Scanner(System.in);

    int n = scan.nextInt();

    int sum = 0;

    for(int i=1; i<=n; i++){

    sum = sum + (int)Math.pow(i, 2);

    }

     System.out.println(sum);

  }

}

**Explanation:**

1. The code begins by importing the required classes, `java.util.*`, which includes the Scanner class.

2. The `Main` class is defined.

3. The `main` method is the entry point of the program.

4. The code creates a Scanner object `scan` to read input from the user.

5. The variable `n` is initialized by reading an integer from the user using `scan.nextInt()`.

6. The variable `sum` is initialized to 0. This variable will store the sum of squares of numbers.

7. The code enters a for loop that iterates from `i = 1` to `i = n`.

8. Inside the loop, `Math.pow(i, 2)` calculates the square of the current number `i` and returns a double value.

9. `(int)` is used to cast the result of `Math.pow(i, 2)` to an integer to store it in the `sum` variable.

10. The calculated square is added to the `sum` variable using the `+=` operator.

11. After the loop ends, the final value of `sum` is printed using `System.out.println(sum)`.

12. The program execution ends.

Overall, the code calculates the sum of squares of numbers from 1 to `n` and prints the result.

---

**Problem 2:**

Problem Statement:

**The Cuckoo Sequence**

A Cuckoo Sequence is defined as shown.

Cuckoo[1]=0

Cuckoo[2]=1

Cuckoo[n]=1*Cuckoo[n-1]+2*Cuckoo[n-2]+3*1, for n>2

Given n(1<= n <=10^8), find Cuckoo[n].

**Input Specification:**

**Input1:** Integer n

**Output Specification:**

Return the value of Cuckoo[n]

**Example:**

Input: 3

Output: 4

Explanation: cuckoo(3) = 1*cuckoo(2) + 2*cuckoo(1) + 3*1

= 1*1 + 2*0 + 3 = 4

**Code:**

import java.util.*;

class Main

{

  public static void main(String args[])

  {

    Scanner scan = new Scanner(System.in);

    int n = scan.nextInt();

    int res = cuckoo(n);

    System.out.println(res);

  }

  public static int cuckoo(int n ){

  if(n==1){

  return 0;

  }

  else if (n==2){

  return 1;

  }

   else{

   return 1*cuckoo(n-1) + 2*cuckoo(n-2) + 3*1;

   }

  }

}

**Explanation:**

Code calculates the result of a recursive function `cuckoo()` and prints the result.

1. The code begins by importing the required classes, `java.util.*`, which includes the Scanner class.

2. The `Main` class is defined.

3. The `main` method is the entry point of the program.

4. The code creates a Scanner object `scan` to read input from the user.

5. The variable `n` is initialized by reading an integer from the user using `scan.nextInt()`. This value represents the input to the `cuckoo()` function.

6. The code calls the `cuckoo()` function with `n` as an argument and stores the result in the variable `res`.

7. Finally, the result `res` is printed using `System.out.println(res)`.

8. The `cuckoo()` function is defined outside the `main` method and takes an integer `n` as input.

9. The function checks for base cases using if-else conditions. If `n` is equal to 1, the function returns 0. If `n` is equal to 2, the function returns 1.

10. If none of the base cases match, the function uses recursion to calculate the result. The formula `1*cuckoo(n-1) + 2*cuckoo(n-2) + 3*1` is used to compute the result.

11. The function recursively calls itself with `n-1` and `n-2` as arguments and multiplies the results by 1 and 2, respectively. The final term `3*1` is added to the calculation.

12. The calculated result is returned by the function.

13. The program execution ends.

Overall, the code calculates the result of the `cuckoo()` function using recursion and prints the result. The function follows a specific formula based on the value of `n` to calculate the result.