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

# Longest Increasing Subsequence(LIS)

Given an array of integers, find the length of the longest (strictly) increasing subsequence from the given array.

Input:
N = 16
A[]={0,8,4,12,2,10,6,14,1,9,5
     13,3,11,7,15}
Output: 6
Explanation:Longest increasing subsequence
0 2 6 9 13 15, which has length 6


## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://practice.geeksforgeeks.org/problems/longest-increasing-subsequence-1587115620/1#<br/>
  Genre : DP || Memorization  <br/>

## Solution: 
DP
```
      public static int longestSubsequence(int size, int a[]) {
        int[] dp = new int[size]; //dp[i] signifies that what the max longest subsequence if we incl ith element
        dp[0]=1;
        for(int i=1;i<size;i++) {
            for(int j=0;j<i;j++) {
                if(a[j]<a[i]) dp[i]=Math.max(dp[i],dp[j]);
            }
            dp[i]+=1;
        }
        int ret=0;
        for(int b:dp) ret=Math.max(ret,b);
            // System.out.print(b+" ");
        return ret;
        
        
    }
```
TC - O(n<sup>2</sup>)

**we can solve this with O(n log(n)) using binery search**

DP with binery search
```
      public static int LIS(int size, int a[]) {
        int[] tail = new int[size]; //tail[i] signifies highest smallest LCS till ith index
        int len=1;
        tail[0]=a[0];
        for(int i=1;i<size;i++) {
            if(a[i] > tail[len-1]) {
              tail[len]=a[i];
              len++;
            } else {
              int c = upper_bound(tail,0,len-1,a[i]);
              tail[c]=a[i];
            }
        }
        return len;
    }
    
        static int upper_bound(int tail[], int l, int r, int key) { 
            while (r > l) {         
                int m = l + (r - l) / 2; 
                if (tail[m] >= key) 
                    r = m; 
                else
                    l = m+1; 
            } 
      
            return r; 
        } 

```
# Longest Decreasing Subsequence(LCS)

Given an array of integers, find the length of the longest (strictly) decreasing subsequence from the given array.

Input:
A[]={5, 0, 3, 2, 9}
Output: 3
Explanation:Longest decreasing subsequence
5, 3, 2, which has length 3


## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://www.codingninjas.com/codestudio/problems/longest-decreasing-subsequence_800300<br/>
  Genre : DP || Memorization || Binery Search <br/>

## Solution: 

```
public static int LDS(int n, int a[]) {
  int[] dp= new int[n];
  dp[n-1]=1;
  for(int i=n-2;i>=0;i--) {
    for(int j=n-1;j>i;j--) {
      if(a[j]<a[i]) dp[i]=Math.max(dp[i],dp[j]);
    }
    dp[i]+=1;
  }
}
```
