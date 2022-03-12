<h1>Reverse Pairs</h1>

## About Problem 
  Difficulty : Hard<br/>
  Problem link: https://leetcode.com/problems/reverse-pairs<br/>
  Genre : Merge Sort  <br/>
  Solution: 
  
## Problem Statement
Given an integer array nums, return the number of reverse pairs in the array.

A reverse pair is a pair (i, j) where 0 <= i < j < nums.length and nums[i] > 2 * nums[j].

## Intution 
Count inversions during Merge Sort. Here the definition of an inversion is slightly changed but core idea remains the same.

## Code
Here i used new types of mergesort technique
 ```
  class Solution {
    public int reversePairs(int[] nums) {
        return divide(nums,new int[nums.length],0,nums.length-1);
    }
    
    public int divide(int[] nums,int[] temp,int l,int r) {
        int ans=0;
        if(l<r) {
            int mid = (l+r)>>1;
            ans+=divide(nums,temp,l,mid);
            ans+=divide(nums,temp,mid+1,r);
            
            ans+=merge(nums,temp,l,mid,r);
            
        }
        return ans;
    }
    public  int merge(int[] A, int[] M, int l, int m, int r) {
      int i = l, t = l, k = 0, res = 0;
      for(int j = m + 1; j <= r; j++) {
        while(t <= m && A[t] <= 2L * A[j]) {
          t++;
        }
        res += m - t + 1;
        while(i <= m && A[i] <= A[j]) {
          M[k++] = A[i++];
        }
        M[k++] = A[j];
      }
      while(i <= m) {
        M[k++] = A[i++];
      }
      for(i = l; i <= r; i++) {
        A[i] = M[i - l];
      }
      return res;
    }
    
}
 ```
