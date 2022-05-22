# Facts

### Stack vs ArrayDeque
 1. both have same functionally like push, pop, etc.
 2. [Stack is synchronized-(thread safe) while ArrayDeque is asynchronized.](https://github.com/tanuj1811/damn_dsa/blob/main/Sync%20vs%20Async.md)
 3. Stack inherits vector -> list -> collections in heirachy while ArrayDeque inherits ArrayDeque -> Deque -> Queue -> Collections.
 4. ArrayDeque is faster because of its async nature and can insert and delete at its both ends

**Prefer ArrayDeque is your contents for faster result.**

**The main application of stack is monotonic stack**

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


## Stock span Problem
Design an algorithm that collects daily price quotes for some stock and returns the span of that stock's price for the current day.

The span of the stock's price today is defined as the maximum number of consecutive days (starting from today and going backward) for which the stock price was less than or equal to today's price.

For example, if the price of a stock over the next 7 days were [100,80,60,70,60,75,85], then the stock spans would be [1,1,1,2,1,4,6].
Implement the StockSpanner class:

StockSpanner() Initializes the object of the class.
int next(int price) Returns the span of the stock's price given that today's price is price.

```
Input
["StockSpanner", "next", "next", "next", "next", "next", "next", "next"]
[[], [100], [80], [60], [70], [60], [75], [85]]
Output
[null, 1, 1, 1, 2, 1, 4, 6]

Explanation
StockSpanner stockSpanner = new StockSpanner();
stockSpanner.next(100); // return 1
stockSpanner.next(80);  // return 1
stockSpanner.next(60);  // return 1
stockSpanner.next(70);  // return 2
stockSpanner.next(60);  // return 1
stockSpanner.next(75);  // return 4, because the last 4 prices (including today's price of 75) were less than or equal to today's price.
stockSpanner.next(85);  // return 6
```

### About Problem 
  Difficulty : Easy<br/>
  [Problem link](https://www.codingninjas.com/codestudio/problems/n-stacks-in-an-array_1164271)
  
  Genre : Stack <br/>
### Solution


```
class StockSpanner {
    ArrayDeque<int[]> ad;
    public StockSpanner() {
        ad=new ArrayDeque<>();
    }
    
    public int next(int price) {
        int i=1;
        while(!ad.isEmpty() && ad.peek()[0]<=price) 
            i+=ad.pop()[1];
        ad.push(new int[] {price,i});
        return i;
    }
}
```

 


