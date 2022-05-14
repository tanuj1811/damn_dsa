<h1>0-1 knapsack problem</h1>

## About Problem 
**Its a NP (nondeterministic polynomial) hard Problem**
  Difficulty : Medium<br/>
  Problem link: https://practice.geeksforgeeks.org/problems/0-1-knapsack-problem0945/1/  <br/>
  Genre : DP  <br/>
  Solution: 
  
## Problem Statement
You are given weights and values of N items, put these items in a knapsack of capacity W to get the maximum total value in the knapsack. Note that we have only one quantity of each item.
In other words, given two integer arrays val[0..N-1] and wt[0..N-1] which represent values and weights associated with N items respectively. Also given an integer W which represents knapsack capacity, find out the maximum value subset of val[] such that sum of the weights of this subset is smaller than or equal to W. You cannot break an item, either pick the complete item or dont pick it (0-1 property).

## code

```
//Function to return max value that can be put in knapsack of capacity W.
    public int knapSack(int w, int wt[], int val[], int n) { 
         int[][] dp = new int[n+1][w+1];
         
         for(int i=1;i<=n;i++) {
             for(int j=1;j<=w;j++) {
                 if(wt[i-1]<=j){
                     dp[i][j]=Math.max(val[i-1]+ dp[i - 1][j - wt[i - 1]],dp[i - 1][j]);
                 }else dp[i][j] = dp[i-1][j];
             }
         }
         
         return dp[n][w];
         
    } 
```

# Ones and Zeroes

## About Problem 
**Its a NP (nondeterministic polynomial) hard Problem**
  Difficulty : Medium<br/>
  Problem link: https://leetcode.com/problems/ones-and-zeroes/  <br/>
  Genre : DP  <br/>
  Solution: 
  
## Problem Statement
You are given an array of binary strings strs and two integers m and n.

Return the size of the largest subset of strs such that there are at most m 0's and n 1's in the subset.

A set x is a subset of a set y if all elements of x are also elements of y.
```
Input: strs = ["10","0001","111001","1","0"], m = 5, n = 3
Output: 4
Explanation: The largest subset with at most 5 0's and 3 1's is {"10", "0001", "1", "0"}, so the answer is 4.
Other valid but smaller subsets include {"0001", "1"} and {"10", "1", "0"}.
{"111001"} is an invalid subset because it contains 4 1's, greater than the maximum of 3.
```
## code
```
class Solution {
    public int findMaxForm(String[] strs, int m, int n) {
        int[][] dp = new int[m+1][n+1];
        for (String s : strs) {
            int[] count = count(s);
            for (int i=m;i>=count[0];i--) 
                for (int j=n;j>=count[1];j--) 
                    dp[i][j] = Math.max(1 + dp[i-count[0]][j-count[1]], dp[i][j]);
        }
        return dp[m][n];
    }

    public int[] count(String str) {
        int[] res = new int[2];
        for (int i=0;i<str.length();i++)
            res[str.charAt(i) - '0']++;
        return res;
     }
}
```
