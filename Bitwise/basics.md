## BITS MANIPULATION

There are mainly 5 types of bitwise operation we usually used in dsa and cp :-
* AND ('&')
* OR ('|')
* XOR('^')
* Right Shift ('<<')
* Left Shift('>>')

As we already study about AND, OR and XOR and that's is but we will how to use them in different ques ? in the upcoming blogs 😊
![image](https://fresh2refresh.com/wp-content/uploads/2013/10/Truth-table-2.png)

Some common tips 

#### Right Shift and Left Shift
Right shift of any no means dividing that number by 2 and Left shift of any number means multiplying by 2

let take exapmle, n=11(1101)
if we one right shift the operator
n>>1
1101>>1 = 0110
which futher equal to 5 (coz it take int value not float value)
n<<1
1101<<1 = 11010
which is equal to 22 in decimal

More General we can say
Left Shift of n by x (n<<x) equals to <b>n*(2<sup>x</sup>)</b>.

Similarly, Right Shift of n by x (n>>x) equals to n/2<sup>x</sup>.

That's all about basic 

Let's take some ques where can apply all 5 logics

### How many bits n contains ?

input 1: 11
output: 4

imput 2: 16
output 5

if you are not fimiler with bits usually do 
1. Convert that interger to binery string (Integer.toBineryString(n)) and send length
boring and take more time.

People who familier with bit manupulation
1. Use Right shift util n become zero.
  ```
    while(n!=0) {
      bit++;
      n=n>>1; or n/=2;
    }
    
  ```
 TC-log(n) as simple
 
 People with insane level skills 
 As we all know above time complexity is log(n). So, if analize the pattern we figured out O(1) soln
 
 Total bits n contains is (log<sub>2</sub>n)+1
 
 ```
    return Math.log(11,2)+1;
 ```
 
 For understading this let's take example 
 
(log<sub>10</sub>10)
(log<sub>10</sub>100)
so all numbers b/w 10 to 99 is gives 1 as int
(log<sub>10</sub>76) = 1

no of digit contains by 76 = (log<sub>10</sub>76) + 1 = 1+1=2

Similarly, apply in log base 2

(log<sub>2</sub>11) = 3

Hence, no of bits contains by 11 = (log<sub>2</sub>11) + 1 = 3+1= 4

### Count no of set bits (imp.)

2. Now you are familier with bits don't need first step
```
  while(n!=0) {
    if(n%2==0) setBit++; // if n is even its never have last bit as 1
    n=n>>1;
  }

```
OR
```
  while(n!=0) {
    if(n&1==1) setBit++; // & of 1 and 1 is always 1
    n=n>>1;
  }

```
That's all...😊
