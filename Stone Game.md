<h1> Stone Game</h1>

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://leetcode.com/problems/stone-game/<br/>
  Genre 😂: Greedy (just only result), DP (max stones found) ,Game Theory<br/>
  Solution: 
   
   ## Approach Discussion
   
   When i read the problem the 1st think come in the mind is wrong greedy approach i.e
   "Just found the maximum b/w both the ends and store in variable if the player has max stones then he wins.
    e.g: [3,7,2,3] player1:3+3=6 palyer2=7+2=9
    player2 wins but that's wrong 
    player1 can win he select like 3(from last)+7
    
   Here 2nd greedy comes in my mind i.e there is always possiblity that player1 can win 
      So, i just
          ```return true```  😂
     and that work's.
     
   But, as we all know it's not what ques demand i think more and more 
   and 3rd greedy comes in my mind. You think this is crazy greedy greedy kr dia bas chod de bhai but
   if there is little modification on the problem statement i.e 
   
   instead of telling player1 can win or not if there is how?and max stones? then divide method different approach we need
   
   for how => we use 3rd greedy😒😁 i.e find sum of all odds and sum of all even indexes which is max player1 choose that part 
   e.g [20, 30, 2, 1, 10] sum_of_even-idxes( w.r.t 1-based index )= 30+1=31 and simararly odd_idxes=20+2+10=32 
   odd_one is max So, player1 force or make the situation that player2 only choose even indexes
   
   and for max stones => there is DP and explaination is in this ``` https://youtu.be/ww4V7vRIzSk ``` video.
   
   ## Code
   ```
    class Solution {
      int[][] dp;
      public boolean stoneGame(int[] piles) {
          dp=new int[piles.length][piles.length];
          System.out.println(helper(piles,0,piles.length-1));
          return true;
      }

      public int helper(int[] arr,int l,int r) {
          if(l>=r) return 0;
          if(dp[l][r]!=0) return dp[l][r];

          return dp[l][r]=Math.max(
              arr[l]+Math.min(helper(arr,l+2,r),helper(arr,l+1,r-1)),
              arr[r]+Math.min(helper(arr,l+1,r-1),helper(arr,l,r-2)));
      }
    }
   ```
   ----------------- ANOTHER SOLUTION FROM DISSCUSSION ----------------- <br/>
   this is because in my code i think dp isn't working well
   ```
   public static int gameOnIntTD(int[] piles, int si, int ei, boolean turn, int[][] strg){
      if(si > ei){
        return 0;
      }

      // If the Recursion has Calculated the Answer  
      if(strg[si][ei] > 0){
        return strg[si][ei]; // return that Stored Answer
      }

      if(turn){ // If it is Alex's Turn
        int rr1 = gameOnIntTD(piles, si + 1,ei,false, strg) + piles[si]; 
        int rr2 = gameOnIntTD(piles, si,ei - 1,false, strg) + piles[ei]; 
        strg[si][ei] = Math.max(rr1, rr2); // Storing the max ans at particular indices
        return strg[si][ei];
      }
      // If it is Lee's Turn
      int rr1 = gameOnIntTD(piles, si + 1, ei, true, strg) - piles[si]; //Same logic as above
      int rr2 = gameOnIntTD(piles, si, ei - 1, true, strg) - piles[ei];//Same logic as above
      strg[si][ei] = Math.min(rr1, rr2); //Storing the answer at particular indices
      return strg[si][ei];
    }
   ```
