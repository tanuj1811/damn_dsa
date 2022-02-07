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
   ```
