# Longest Common Subsequence

Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.

For example, "ace" is a subsequence of "abcde".

## About Problem 
  Difficulty : Easy<br/>
  Problem link: https://leetcode.com/problems/longest-common-subsequence/<br/>
  Genre : DP || Memorization  <br/>

## Solution: 

DP Solution
```
    public int longestCommonSubsequence(String text1, String text2) {
        int n = text1.length(), m = text2.length();
        int[][] dp = new int[n+1][m+1];
        
        for(int i = n-1;i>=0;i--){
            for(int j = m-1;j>=0;j--){
                if(text1.charAt(i) == text2.charAt(j))
                    dp[i][j] = 1 + dp[i+1][j+1];
                else
                    dp[i][j] = Math.max(dp[i+1][j],dp[i][j+1]);
            }
        }
        return dp[0][0];
    }
```
TC - O(n<sup>2</sup>

Recursion With Memo.
```
    int[][] mem;
    public int longestCommonSubsequence(String text1, String text2) {
        mem = new int[text1.length()][text2.length()];
        return rec(text1,text2,0,0);
    }
    
    public int rec(String a, String b, int i, int j) {
        if(i>=a.length() || j>=b.length()) return 0;
        if(mem[i][j]!=0) return mem[i][j];
        int ret=0;
        if(a.charAt(i)==b.charAt(j)) ret= 1+rec(a,b,i+1,j+1);
        else {
            ret=Math.max(rec(a,b,i,j+1), rec(a,b,i+1,j));
        }
        
        return mem[i][j]=ret;
    }
```
