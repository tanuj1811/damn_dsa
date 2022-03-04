<h1> Sum of two numbers without using arithmetic operators </h1>

## About Problem 
  Difficulty : Medium<br/>
  Problem link: https://practice.geeksforgeeks.org/problems/sum-of-two-numbers-without-using-arithmetic-operators/1/?track=md-bm<br/>
  Genre : Bit Manupulation <br/>
  Solution: 
  
## Problem Statement
  Given two integers a and b. Find the sum of two numbers without using arithmetic operators.
  
## Approach
I think we all familier with 
AUB=A+B - A∩B
So, A+B=AUB+A∩B
Here's U->Union->'&' and ∩->Intersection->'|'
A+B= A&B + A|B

Let take example A=4 and B=8

A+B= 4&8 + 4|8
A+B = 0+12 = 12

```
  return A&B + A|B;
```

1 entity later 
I figured out we are still using '+' symbol 😣

#### Approach 2
This is serious approach you need your full concertation

This approach starts with normal bit adding <br>
![image](https://user-images.githubusercontent.com/54256549/156704909-6fe42e93-69ce-4982-a4b1-2e39f9eaf3f5.png) <br>

Why using xor and adding it to ans ??
i use xor their for adding the new set bit to ans.

If xor is used for adding why doing these much stuff just xor A and B

No, xor of 5 and 3 = 6 not 8 
but xor logic is working in my case because 

i am any number just adding 10, 100, 1000, 10000.....
ans is always smaller than Math.pow(2,i) beacuse i is increasing
10000^1010 = 11010 won't effect and other just put 1 at Most Significant Place

### CODE
```
/**
*Note, Here ++ is increment operator not athithmatic operator
*/
  public int sum(int a , int b) {
        
        int carry=0; // as carry is either 0 or 1
        int i=0; //holding position 
        int ans=0;
        while(a!=0 || b!=0) {
            // int adding_at_pos_i=(a&1)+(b&1)+carry; // this adding which is breaking the noams
            int adding_at_pos_i=0;           
            if((a&1)==1) adding_at_pos_i++;
            if((b&1)==1) adding_at_pos_i++;
            if(carry==1) adding_at_pos_i++;
            carry=adding_at_pos_i/2;
            if(adding_at_pos_i%2==1) 
                ans^= (1<<i); // Math.pow(2,i);
            i++;
            a=a>>1;
            b=b>>1;
        }
        if(carry==1) ans^=1<<i;
        
        return ans;
        
    }
```




