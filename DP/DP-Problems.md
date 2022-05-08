# Longest Common Subsequence(LCS)

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

# Longest Common Subsequence(LCS)

Given a value N, find the number of ways to make change for N cents, if we have infinite supply of each of S = { S1, S2, .. , SM } valued coins

Input:
n = 4 , m = 3
S[] = {1,2,3}
**Output:** 4

Explanation: Four Possible ways are:
{1,1,1,1},{1,1,2},{2,2},{1,3}.

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://practice.geeksforgeeks.org/problems/coin-change2448/1<br/>
  Genre : DP || Memorization  <br/>

## Solution: 
DP
```
// dp[i][j] : No. of combinations we can get with sum i and coins from 1 to j
    public long count(int c[], int m, int n) {
        long[][] dp = new long[n+1][m+1];
        for(int i=1;i<=n;i++) dp[i][0]=0;
        for(int j=0;j<=m;j++) dp[0][j]=1;
        
        for(int i=1;i<=n;i++) {
            for(int j=1;j<=m;j++) {
                dp[i][j]=dp[i][j-1];
                if(c[j-1]<=i) dp[i][j]+=dp[i-c[j-1]][j];
            }
        }
        return dp[n][m];
    }
```
Recursion with Memorisation
```
    long[][] mem;
    public long count(int S[], int m, int n) {
        mem= new long[n+1][m+1];
        for(int i=0;i<=n;i++)
        for(int j=0;j<=m;j++) mem[i][j]=-1;
        return rec(S,n,0);
    }
    
    public long rec(int[] c,int a,int i) {
        if(a<0 || i>= c.length) return 0;
        if(a==0) return 1L;
        if(mem[a][i]!=-1) return mem[a][i];
        long incl=0,notIncl=0;
        if(c[i]<= a)
            incl = rec(c,a-c[i],i);
        
        notIncl = rec(c,a,i+1);
        return mem[a][i]=notIncl+ incl;
        
    }
```
