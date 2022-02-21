<h1>Majority Element || Boyer-Moore Voting Algorithm</h1>

## About Problem 
  Difficulty : Easy<br/>
  Problem link: https://leetcode.com/problems/majority-element/<br/>
  Genre : Logic <br/>
  Solution: 
  
## Problem Statement
Given an array nums of size n, return the majority element.
The majority element is the element that appears more than ⌊n / 2⌋ times.

## Approach Discussion
The first and common approach for solving this ques is brute force 
i.e :: 1st fix an no. then find the freq. If freq we get is greater than n/2 then return no.
tc:- O(n^2) and sc:-O(1)

2nd approach is using map
i.e :: calc the freq of all number then iterator the map and return the no that freq is greater than n/2

3rd approach is using Boyer-Moore Voting Algorithm
In this, its uses the n/2 i.e :: we all know if a number repeats its half of the array which means its takes advantage.

## Code

```  
public int majorityElement(int[] nums) {
       int count=0,maxrepeating=0;
       for(int num:nums) {
       if(count==0)
           maxrepeating=num;
       if(num==maxrepeating) count+=1;
       else count-=1;
    }
    return maxrepeating;  
 }  
```
## Intution
let's the array 
 [1,1,2,3,1,1,2,2,3,4,1,1,1,1,3] 
 
 count == 0  signifies that before that majority element is equals to other element so we need to make change majority element.
 
 
