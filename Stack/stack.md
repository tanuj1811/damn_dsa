# Facts

### Stack vs ArrayDeque
 1. both have same functionally like push, pop, etc.
 2. [Stack is synchronized-(thread safe) while ArrayDeque is asynchronized.](https://github.com/tanuj1811/damn_dsa/blob/main/Sync%20vs%20Async.md)
 3. Stack inherits vector -> list -> collections in heirachy while ArrayDeque inherits ArrayDeque -> Deque -> Queue -> Collections.
 4. ArrayDeque is faster because of its async nature and can insert and delete at its both ends

**Prefer ArrayDeque is your contents for faster result.**

# Problems

## 2 stack in an array
```
Input:
push1(2)
push1(3)
push2(4)
pop1()
pop2()
pop2()

Output:
3 4 -1

Explanation:
push1(2) the stack1 will be {2}
push1(3) the stack1 will be {2,3}
push2(4) the stack2 will be {4}
pop1()   the poped element will be 3 
from stack1 and stack1 will be {2}
pop2()   the poped element will be 4 
from stack2 and now stack2 is empty
pop2()   the stack2 is now empty hence -1 .
```

### About Problem 
  Difficulty : Easy<br/>
  [Problem link](https://practice.geeksforgeeks.org/problems/implement-two-stacks-in-an-array/1/)<br/>  
  Genre : Stack <br/>
  
### Solution
```
/* Structure of the class is
class TwoStack
{

	int size;
	int top1,top2;
	int arr[] = new int[100];

	TwoStack()
	{
		size = 100;
		top1 = -1;
		top2 = size;
	}
}*/

class Stacks
{
    
    //Function to push an integer into the stack1.
    void push1(int x, TwoStack sq)
    {
        if(sq.top1<sq.top2) {
            sq.top1+=1;
            sq.arr[sq.top1]=x;
        }
    }

    //Function to push an integer into the stack2.
    void push2(int x, TwoStack sq)
    {
        if(sq.top1<sq.top2) {
            sq.top2-=1;
            sq.arr[sq.top2]=x;
        }
    }

    //Function to remove an element from top of the stack1.
    int pop1(TwoStack sq)
    {
        if(sq.top1==-1) return -1;
        sq.top1-=1;
        return sq.arr[sq.top1+1];
        
        
    }

    //Function to remove an element from top of the stack2.
    int pop2(TwoStack sq)
    {
        if(sq.top2==100) return -1;
        sq.top2+=1;
        return sq.arr[sq.top2-1];
        
    }
}
```
## N stack in an array
Design a data structure to implement ‘N’ stacks using a single array of size ‘S’. It should support the following operations:

push(X, M): Pushes an element X into the Mth stack. Returns true if the element is pushed into the stack, otherwise false.

pop(M): Pops the top element from Mth Stack. Returns -1 if the stack is empty, otherwise, returns the popped element.



### About Problem 
  Difficulty : Easy<br/>
  [Problem link](https://www.codingninjas.com/codestudio/problems/n-stacks-in-an-array_1164271)
  
  Genre : Stack <br/>
### Solution

```
```




 


