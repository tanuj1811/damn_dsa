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

# Sort the Linked List
```
Input: head = [4,2,1,3]
Output: [1,2,3,4]
```

## About Problem 
  Difficulty : Easy<br/>
  [Problem link](https://leetcode.com/problems/sort-list/)
  
  Genre : MergeSort <br/>
## Solution
```
class Solution {
    public ListNode sortList(ListNode head) {
        return divide(head);
    }
    
    public ListNode divide(ListNode head) {
        if(head==null || head.next==null) return head;
        ListNode mid = getMid(head);
        ListNode left=divide(head);
        ListNode right=divide(mid);
        return merge(left,right);
        // return right;
    }
    
    public ListNode merge(ListNode l1,ListNode l2) {
        ListNode ans=new ListNode(-1);
        ListNode ret=ans;
        
        while(l1!=null && l2!=null) {
            if(l1.val < l2.val) {
                ans.next=new ListNode(l1.val);
                l1=l1.next;
            } else {
                ans.next=new ListNode(l2.val);
                l2=l2.next;
            }
            ans=ans.next;
        }
        while(l1!=null) {
            ans.next=new ListNode(l1.val);
            l1=l1.next;
            ans=ans.next;
        }
        while(l2!=null) {
            ans.next=new ListNode(l2.val);
            l2=l2.next;
            ans=ans.next;
        }
        return ret.next;
    }
    
    public ListNode getMid(ListNode head) {
        ListNode slow=new ListNode(-1,head),fast=head;
        while(fast!=null&&fast.next!=null) {
            slow=slow.next;
            fast=fast.next.next;
        }
        ListNode ret=slow.next;
        slow.next=null;
        return ret;
    }
}
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

# Reverse the LinkedList II

You are given the head of a singly linked-list. The list can be represented as:
```
L0 → L1 → … → Ln - 1 → Ln
```
Reorder the list to be on the following form:
```
L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …
```
You may not modify the values in the list's nodes. Only nodes themselves may be changed.

```
Input: head = [1,2,3,4,5]
Output: [1,5,2,4,3]
```

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://leetcode.com/problems/reorder-list/ br/>
  Genre : Brain || visualization  <br/>

## Solution: 
```
class Solution {
    public void reorderList(ListNode head) {
        ListNode slow = head;
        ListNode fast = head.next;
        while(fast!=null && fast.next!=null) {
            slow=slow.next;
            fast=fast.next.next;
        }
        ListNode tmp = slow.next;
        slow.next=null;
        ListNode first = head;
            
        //reverse the second
        ListNode second = reverseList(tmp);
        
        //merge
        ListNode res = new ListNode();
        head=res;
        while(second!=null && first!=null) {
            res.next = first;
            res=res.next;
            first = first.next;
            res.next=second;
            res=res.next;
            second=second.next;
            
        }
        while(second!=null) {
            res.next=second;
            second=second.next;
            res=res.next;
        }
        while(first!=null) {
            res.next=first;
            first=first.next;
            res=res.next;
        }
        
        
    }
    
    public ListNode reverseList(ListNode head) {
        if(head==null || head.next==null)
            return head;
        ListNode nextNode=head.next;
        ListNode newHead=reverseList(nextNode);
        nextNode.next=head;
        head.next=null;
        return newHead;
    }
}
```

# Flatten a Multilevel Doubly Linked List

You are given a doubly linked list, which contains nodes that have a next pointer, a previous pointer, and an additional child pointer. This child pointer may or may not point to a separate doubly linked list, also containing these special nodes. These child lists may have one or more children of their own, and so on, to produce a multilevel data structure as shown in the example below.

Given the head of the first level of the list, flatten the list so that all the nodes appear in a single-level, doubly linked list. Let curr be a node with a child list. The nodes in the child list should appear after curr and before curr.next in the flattened list.

Return the head of the flattened list. The nodes in the list must have all of their child pointers set to null.

![image](https://user-images.githubusercontent.com/54256549/169660898-c9a41499-8115-448c-ac6b-3129e7e47668.png)


## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/<br/>
  Genre : Brain || visualization  <br/>

## Solution: 

```
/*
// Definition for a Node.
class Node {
    public int val;
    public Node prev;
    public Node next;
    public Node child;
};
*/

```

```
class Solution {
    public Node flatten(Node head) {
        Node dummy=new Node(-1);
        dummy.next=head;
        
        while(dummy!=null) {
            dummy=dummy.next;
            if(dummy==null) break;
            if(dummy.child==null) continue;
            Node child = dummy.child;
            while(child.next!=null) child=child.next;
            child.next=dummy.next;
            if(dummy.next!=null)dummy.next.prev=child;
            dummy.next=dummy.child;
            dummy.child.prev=dummy;
            dummy.child=null;
        }
        return head;
    }
}
```
