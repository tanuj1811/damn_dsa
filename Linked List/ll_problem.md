```
/**
 * Definition for singly-linked list.
public class ListNode {
    int val;
    ListNode next;
    ListNode() {}
    ListNode(int val) { this.val = val; }
    ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 }
 */
```
# Reverse the LinkedList

```
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

## About Problem 
  Difficulty : Easy<br/>
  Problem link: https://leetcode.com/problems/reverse-linked-list/<br/>
  Genre : Brain || visualization  <br/>

## Solution: 
```
class Solution {
    
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode next = head;
        // ListNode ret=head;
        while(next!=null) {
            ListNode cur=next;
            next=cur.next;
            cur.next=prev;
            prev=cur;
        }
        
        return prev;
    }
}
```

# Reverse the LinkedList II

Given the head of a singly linked list and two integers left and right where left <= right, reverse the nodes of the list from position left to position right, and return the reversed list.

```
Input: head = [1,2,3,4,5], left = 2, right = 4
Output: [1,4,3,2,5]
```

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://leetcode.com/problems/reverse-linked-list-ii/<br/>
  Genre : Brain || visualization  <br/>

## Solution: 

```
class Solution {
    public ListNode reverseBetween(ListNode head, int left, int right) {
        /**
            Step to acheive
                1. dummy to store head
                2. take prevLeft pointer to the left-1th Node and current pointer to Node where we have to reverse
                3. reverse the range right-left
                4. update the pointer to point final step
        */
        ListNode dummy=new ListNode(-1,head);
        ListNode leftPrev=dummy,cur=head,prev=null;
        
        for(int i=0;i<left-1;i++) {
            leftPrev=leftPrev.next;
            cur=cur.next;
        }
        
        for(int i=0;i<=right-left;i++) {
            ListNode next = cur.next;
            cur.next = prev;
            prev = cur;
            cur = next;
        }
        
        leftPrev.next.next = cur;
        leftPrev.next = prev;
        
        return dummy.next;
    }
}
```

# Add Two Number

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Left to right**

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://leetcode.com/problems/add-two-numbers/<br/>
  Genre : Brain || visualization  <br/>

## Solution: 

```
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode ans=new ListNode(0);
        ListNode ret = ans;
        int carry = 0;
        while(l1!=null || l2!=null) {
            int t = carry; //total
            if(l1!=null) {
                t+=l1.val;
                l1=l1.next;
            }
            if(l2!=null) {
                t+=l2.val;
                l2=l2.next;
            }
            carry=0;
            if(t>9) {
                carry=1;
                t%=10;
            }
            ans.next = new ListNode(t);
            ans=ans.next;
        }
        
        if(carry!=0) ans.next = new ListNode(1);
        
        return ret.next;
    }
}
```

# Add Two Number II

You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Right to left**

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://leetcode.com/problems/add-two-numbers-ii/<br/>
  Genre : Brain || visualization  <br/>

## Solution: 
```
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        /**
        step to do
            1. reverse the both linked list 
            2. add reversed linked list
            3. reverse the answer
        */
        ListNode r1 = reverse(l1);
        ListNode r2 = reverse(l2);
        return reverse(add(r1,r2));
        
    }
    
    public ListNode reverse(ListNode l) {
        ListNode c = l, prev=null ;
        while(c!=null) {
            ListNode n= c.next;
            c.next=prev;
            prev = c;
            c=n;
        }
        return prev;
    }
    public ListNode add(ListNode l1, ListNode l2) {
        ListNode ans=new ListNode(0);
        ListNode ret = ans;
        int carry = 0;
        while(l1!=null || l2!=null) {
            int t = carry;
            if(l1!=null) {
                t+=l1.val;
                l1=l1.next;
            }
            if(l2!=null) {
                t+=l2.val;
                l2=l2.next;
            }
            carry=0;
            // System.out.println(t);
            if(t>9) {
                carry=1;
                t%=10;
            }
            ans.next = new ListNode(t);
            ans=ans.next;
        }
        
        if(carry!=0) ans.next = new ListNode(1);
        
        return ret.next;
    }
}
```
