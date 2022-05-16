# Optimal Strategy for a Game 

You are given an array A of size N. The array contains integers and is of even length. The elements of the array represent N coin of values V1, V2, ....Vn. You play against an opponent in an alternating way.

In each turn, a player selects either the first or last coin from the row, removes it from the row permanently, and receives the value of the coin.

You need to determine the maximum possible amount of money you can win if you go first.
Note: Both the players are playing optimally.

```
N = 4
A[] = {5,3,7,10}
Output: 15
Explanation: The user collects maximum
value as 15(10 + 5)
```

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://practice.geeksforgeeks.org/problems/optimal-strategy-for-a-game-1587115620/1/<br/>
  Genre : DP || Memorization  <br/>

## Solution: 

Recursion with Memo
```
class Solution {
    int[][] dp;
    public int maximumAmount(int[] nums) {
        dp=new int[nums.length][nums.length];
        Arrays.stream(dp).forEach(a -> Arrays.fill(a, -1));
        return rec(nums,0,nums.length-1);
    }
    
    public int rec(int[] a,int i,int j) {
        if(i>j) return 0;
        if(i+1==j) return Math.max(a[i],a[j]);
        if(dp[i][j]!=-1) return dp[i][j];
        int starting = a[i]+Math.min(rec(a,i+2,j),rec(a,i+1,j-1)); // we choose a[i] 
        int end = a[j]+Math.min(rec(a,i ,j-2),rec(a,i+1,j-1));
        return dp[i][j]=Math.max(starting, end);
    }
}
```


DP Solution
```
class Solution {
    public int maximumAmount(int[] nums) {
        int[][] dp=new int[nums.length][nums.length];
        Arrays.stream(dp).forEach(a -> Arrays.fill(a, -1));
        
        for(int gap = 0;gap<nums.length;gap+=1) {
            for(int i=0,j=gap;j<nums.length;i++,j++) {
                if(gap == 1) dp[i][j] = Math.max(nums[i],nums[j]);
                else if(gap ==0) dp[i][j] = nums[i];
                else {
                    int starting = nums[i]+Math.min(dp[i+2][j],dp[i+1][j-1]);
                    int ending = nums[j]+Math.min(dp[i][j-2],dp[i+1][j-1]);
                    dp[i][j] = Math.max(starting,ending);
                }
            }
        }
        return dp[0][nums.length-1];
    }
}
```
![image](https://user-images.githubusercontent.com/54256549/168476717-adeb3013-6943-40c4-9aa5-c0373dac978a.png)

# Egg Dropping Puzzle 

You are given k identical eggs and you have access to a building with n floors labeled from 1 to n.

You know that there exists a floor f where 0 <= f <= n such that any egg dropped at a floor higher than f will break, and any egg dropped at or below floor f will not break.

Each move, you may take an unbroken egg and drop it from any floor x (where 1 <= x <= n). If the egg breaks, you can no longer use it. However, if the egg does not break, you may reuse it in future moves.

Return the minimum number of moves that you need to determine with certainty what the value of f is.

```
Input: k = 1, n = 2
Output: 2
Explanation: 
Drop the egg from floor 1. If it breaks, we know that f = 0.
Otherwise, drop the egg from floor 2. If it breaks, we know that f = 1.
If it does not break, then we know f = 2.
Hence, we need at minimum 2 moves to determine with certainty what the value of f is.
```

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://practice.geeksforgeeks.org/problems/egg-dropping-puzzle-1587115620/1/<br/>
                https://leetcode.com/problems/super-egg-drop/<br/>
  Genre : DP || Memorization  <br/>

## Solution: 

**Recursion with Memorization**
TC - O(N<sup>3</sup>)
SC - O(N<sup>2</sup>
```
class Solution 
{
	int[][] dp;
    public int eggDrop(int e, int n) {
        dp=new int[e+1][n+1];
        Arrays.stream(dp).forEach(a -> Arrays.fill(a, -1));
        return rec(e,n);
    }
    public int rec(int e, int n) {
        if(e == 1 || n==0 || n==1) return n;
        if(dp[e][n]!=-1) return dp[e][n];
        int ret=(int)1e7;
        for(int i=1;i<=n;i++) { // can be converted to binery search
            ret = Math.min(ret,Math.max(rec(e-1,i-1),rec(e,n-i)));
        }
        return dp[e][n]=ret+1;
        
    }
}
```
We can use binary search to optimize O(N<sup>3</sup>) to O(N<sup>2</sup>log(n))
```
class Solution {
    int[][] dp;
    public int superEggDrop(int e, int n) {
        dp=new int[e+1][n+1];
        Arrays.stream(dp).forEach(a -> Arrays.fill(a, -1));
        return rec(e,n);
    }
    public int rec(int e, int n) {
        if(e == 1 || n==0 || n==1) return n;
        if(dp[e][n]!=-1) return dp[e][n];
        int l=1,r=n;
        while(l+1<r) {
            int i=(l+r)>>1;
            int breakEgg = rec(e-1,i-1);
            int notbreak = rec(e,n-i);
            
            if(breakEgg < notbreak) l=i;
            else if(breakEgg > notbreak) r=i;
            else l=r=i;
        }
        return dp[e][n]=1+Math.min(Math.max(rec(e-1,l-1),rec(e,n-l)),Math.max(rec(e-1,r-1),rec(e,n-r)));
        
    }
    
    
}
```

