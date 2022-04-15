<h1>Maximum XOR</h1>

## About Problem 
  Difficulty : Maedium<br/>
  Problem link: https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array/<br/>
  Genre : Brute force || Trie <br/>
  Solution: 
  
## Problem Statement
Given an integer array nums, return the maximum result of nums[i] XOR nums[j], where 0 <= i <= j < n.

## Approach Discussion
The simple and brute force aprroach is by using nested 2 for loops

#### Greedy : 
to find maximum xor nums[i] must of maximums in array and nums[j] must be one of minimum in array which is wrong in some cases

#### Main Approach 
Make trie of bit of size 32
```
class Trie {
  Trie zero;
    Trie one; // signifies there is number in which x bit is set or 1
 }
 ```
 ![image](https://user-images.githubusercontent.com/54256549/163561845-8c618bef-684a-4733-8b24-fa364e688726.png)
