<h1> Maximum Height Tree</h1>

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://practice.geeksforgeeks.org/problems/maximum-height-tree4803/1/?page=2&company[]=Walmart&query=page2company[]Walmart<br/>
  Genre : Math <br/>
  Solution: 
  
## Problem Statement
  Given N dots that form a triangle such that ith line contains i number of dots.

      .
     . .
    . . .
   . . . .
   
  Find the minimum hieght H of the triangle that can be formed using these N dots.
   
## Approach Discussion
   
   When i read the problem the 1st think come in the mind is brute force which is
   
   ```
     while(n>0) {
         n-=i++; 
     }
     return n==0?i:i-1;
   ```

   but excepted tc is O(1) So, we need to think more .....⏱️🕝🕒🕜🕑!!
   
   Now after some time i have to go for soln there is very nice O(1) ans lemme show you
   
    n * (n + 1)/2  = x
    n * (n + 1) = 2x
    n^2 + n - 2x = 0;
    as we know ax^2 + bx + c = 0
    after compairing both eqn a = 1,b = 1, c= 2x(x is the input we are getting in hegith funtion)
    D = b^2 - 4ac
    root of eqn i.e n = (-b +- sqrt(b^2 - 4ac)) / 2a;

so now here we are with our final eqn to get the requires solution
        
        int ans = (-1 + Math.sqrt(1 + (8*n))) / 2;
        return ans;
        

   
