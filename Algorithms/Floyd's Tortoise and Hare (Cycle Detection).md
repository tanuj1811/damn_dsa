<h1>Find the Duplicate Number</h1>

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://leetcode.com/problems/find-the-duplicate-number<br/>
  Genre : Brain  <br/>
  Solution: 
  
## Problem Statement
Given an array of integers nums containing n + 1 integers where each integer is in the range [1, n] inclusive.

There is only one repeated number in nums, return this repeated number.

You must solve the problem without modifying the array nums and uses only constant extra space.
 
## Approach Discussion
Simple approach is using Map, or array of size of size n

### Final Approach : Floyd's Tortoise and Hare (Cycle Detection) - youtube -> striver/aayushi sharma
First of all, where does the cycle come from? Let's use the function f(x) = nums[x] to construct the sequence: x, nums[x], nums[nums[x]], nums[nums[nums[x]]], ....

Each new element in the sequence is an element in nums at the index of the previous element.

If one starts from x = nums[0], such a sequence will produce a linked list with a cycle.

The cycle appears because nums contains duplicates. The duplicate node is a cycle entrance.

#### Code
```
/*
  tc->O(n)
  sc->O(1)
*/
class Solution {
    public int findDuplicate(int[] nums) {
        int n=nums.length;
        
        int slow=nums[0];
        int fast=nums[0];
        
        do {
            slow=nums[slow];
            fast=nums[nums[fast];
        } while(slow==fast);
        
        fast=nums[0];
        while(slow!=fast) {
            slow=nums[slow];
            fast=nums[fast];
        }              
        return slow;
            
    }
}
```

### Approach 1 : Negative Marking
This approach leads to modifying the array. So, we have to discard in the end but its best and simple solution among all.
1. Iterate over the array, evaluating each element (let's call the current element curcur).

2. Since we use negative marking, we must ensure that the current element (curcur) is positive (i.e. if curcur is negative, then use its absolute value).

3. Check if nums[cur]nums[cur] is negative.

4. If it is, then we have already performed this operation for the same number, and hence curcur is the duplicate number. Store curcur as the duplicate and exit the loop.

5. Otherwise, flip the sign of nums[cur]nums[cur] (i.e. make it negative). Move to the next element and repeat step 3.

Once we've identified the duplicate, we could just return the duplicate number. However, even though we were not able to meet the problem constraints, we can show that we are mindful of the constraints by restoring the array. This is done by changing all negative numbers to positive.

```
  class Solution {
    public int findDuplicate(int[] nums) {
        int duplicate = -1;
        for (int i = 0; i < nums.length; i++) {
            int cur = Math.abs(nums[i]);
            if (nums[cur] < 0) {
                duplicate = cur;
                break;
            }
            nums[cur] *= -1;
        }
        
        // Restore numbers
        for (int i = 0; i < nums.length; i++)
            nums[i] = Math.abs(nums[i]);

        return duplicate;
    }
}
/*
  tc->O(n)
  sc->O(1)
*/
```

