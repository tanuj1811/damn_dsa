# Recursion 
Recursion is a process of a function calling itself. 

It can cause segmentation fault/stack overflow if the base cases is implemented poorly.

Maximum possible calls is 10<sup>4</sup>.

A program/algo based on a recursive approach is memory-consuming but nowaday's complier convert **tail recursion**( types of recursion) to iterative solution which is faster.

Recursive solution like Quick sort, PreOrder and Inorder treversal are tail recursive program which means they don't occupy memory in stack.

## Tail Recursion
When the last step in a recursive function is the recursive call and here will not any depancy of that recursive call. 

They are faster than normal recursion/non-tail recursion because these kinds of recursive functions are as the compiler replaces the recursive call with the **GOTO** statement.
Hence, no extra memory is needed to store the previous function in the stack.

Recursive solution like Quick sort, PreOrder and Inorder treversal are faster coz they have tail recursive func
Recursion solution like Merge sort and PostOrder traversal are slower in nature and use extra space too.

We can convert some **non-tail** recursive function to **tail recursion** but not all.

#### Non-Tail Recursive Vs Tail Recursive Function

***Non Tail***
```
public int fact(int n) {
  if(n == 0 || n == 1) return 1;
  return n * fact(n-1); // here return function depand upon prev recursive func
}
```
***Tail***
```
public int fact(int n, int k) {
  if(n == 0 || n == 1) return k;
  
  return fact(n-1, k+1);
}
```

# Problems
https://ahampriyanshu.com/dsa-part-5-recursion/
