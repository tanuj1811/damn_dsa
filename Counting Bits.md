<h1>Bitwise Counting</h1>

## About Problem 
  Difficulty : Easy<br/>
  Problem link: https://leetcode.com/problems/counting-bits/<br/>
  Genre : Bitwise | DP  <br/>
  Solution: 
  
## Problem Statement
Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.

## Approach Discussion
The simple and brute force aprroach is take every i and convert it into binary string and count no of 1 in that. 
Acceptable but not efficient 

#### Main Approach 
it will be easy if you understand with example

0 ->0 <br/>
1 ->1 <---- break point<br/> 
2 ->1 <---- //-arly happens here <br/>
3 ->2 <br/>
4 ->1 <---- //-arly happens here<br/>
5 ->2 <br/>
6 ->2 <br/>
7 ->3 <br/>
8 ->1 //-arly happens here <br/>
9 ->2 <br/>
10->2 <br/>
11->3 <br/>
12->2 <br/>
13->3 <br/>
14->3 <br/>
15->4 <br/>
16->1 <br/>

Here ,
the range from 8 to 16 you will understand the logic.


## Code
```
  class Solution {
    public int[] countBits(int n) {
        int[] res =new int[n+1]; // dp
        int range = 1; //2 4 8 16 32 
        
        for(int i=1;i<n+1;i++){
            if(range*2 == i) //jump to new range
                range =i;
            res[i] = 1+res[i-range];
        }
        
        return res;
            
    }
}
```
