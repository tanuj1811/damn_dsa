<h1>XOR-ing the subarray </h1>

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://www.interviewbit.com/problems/xor-ing-the-subarrays/<br/>
  Genre : Bitwise | Observation  <br/>
  Solution: 
  
## Problem Statement
Given an integer array A of size N.

You need to find the value obtained by XOR-ing the contiguous subarrays, followed by XOR-ing the values thus obtained. Determine and return this value.

For example, if A = [3, 4, 5] :

Subarray   Result
3            3
4            4
5            5
3,4   3 XOR 4         7
4,5   4 XOR 5         1
3,4,5    3 XOR 4 XOR 5   2

Now we take the resultant values and XOR them together:

3 ⊕ 4 ⊕ 5 ⊕ 7 ⊕ 1⊕ 2 = 6 we will return 6.

## Approach Discussion

Hint: 3^4^5^3^4^4^5^3^4^5 = 3^5=6

So, question reduces to which number is contributing to answer or which is not.

To check this we have equation :: 
##### Number of times ith element present in the subarray or not = (i+1)*(n-i)

How's it works 
1. First we are calculating subarray starting i-th element suppose y subarray starting with i-th element
2. So, required ans = n-i * y because every prev. element have to through i-th to continue but we know i-th will create y more subarray 
3. So, (n-1)* (i+1) will work

### Code
```
  public class Solution {
    public int solve(ArrayList<Integer> A) {
        int n=A.size();
        int xor=0;
        for(int i=0;i<n;i++) {
            long contri=(i+1)*(n-i);
            if(contri%2==1) xor=(xor^A.get(i));
        }
        return xor;
    }
}

```
