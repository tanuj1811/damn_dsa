<h1>Sort Color || Dutch National Flag Algorithm</h1>

## About Problem 
  Difficulty : Easy<br/>
  Problem link: https://leetcode.com/problems/sort-colors/<br/>
  Genre : arrays <br/>
  Solution: 
  
## Problem Statement
Given an array nums with n objects colored red->0, white->1, or blue->2, sort them in-place so that objects of the same color are adjacent,
with the colors in the order 0, 1, and 2.


## Dutch National Flag - O(n)
```
class Solution {
    public void sortColors(int[] nums) {
        int zero=0;  // It will make sure all element left side of it 0 
        int one=0; //
        int two=nums.length-1; //It will make sure all element right side of it 2
        
        while(one<=two) {
            if(nums[one]==0) {
                swap(nums,zero,one);
                zero++;
                one++;
            }else if(nums[one]==1) {
                one++;
            } else {
                swap(nums,one,two);
                two--;
            }
        }
    }
    public void swap(int[] nums,int i,int j) {
        int t=nums[i];
        nums[i]=nums[j];
        nums[j]=t;
    }
}
```
## Simple O(n)+O(n) Solution
O(n) - for taking freq of all element
O(n) - for filling the array nums
```
class Solution {
    public void sortColors(int[] nums) {
		int[] ar=new int[3]; // freq array stores freq of 0,1.2 w.rt to index
        for(int i:nums) {
            ar[i]++;
        }
        for(int i=0;i<nums.length;i++) {
            if(ar[0]!=0) { // first filling 0
                nums[i]=0;
                ar[0]--;
            } else if(ar[1]!=0) { // then 1
                nums[i]=1;
                ar[1]--;
            } else{ // for filling 2
                nums[i]=2;
                ar[2]--;
            }
            
        }
	}
}
```
