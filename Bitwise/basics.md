## BITS MANIPULATION

### How bit stores in the backend in java 
Java assign 32 bits to every integer.
and Most significant bit(msb) indicate wheather assigned number is -ve or +ve. if msb is 1 then number is -ve

example: 1 = 0000...01 and -1 = 1111....111

**Note** Thats why the range is -2<sup>31</sup> to 2<sup>31</sup>-1 

### Negative Number in bits
In Java, the -ve number is stored as 2's complements representation

Representation of -x : 2<sup>32</sup>-x

Example: suppose given bits = 111..1.1010 === 2<sup>32</sup>-1-5 (-5 coz0...00101 = inverse of given bits, -1 coz its it was in 2's complement) === 2<sup>32</sup>-6

So, x=-6 

### Types of Bit Operation
There are mainly 6 types of bitwise operation we usually used in dsa and cp :-
* Negation('~')
* AND ('&')
* OR ('|')
* XOR('^')
* Signed Right Shift ('>>')
* Unsigned Right Shift('>>>')
* Left Shift('<<')

As we already study about AND, OR and XOR and that's is but we will study how to use them in different ques ? in the upcoming blogs 😊
![image](https://fresh2refresh.com/wp-content/uploads/2013/10/Truth-table-2.png)

Some common tips 
### XOR
as we all know xor of same number is 0.

There is one famous question which is solved using above statement

#### Statement
  Given an array of integers A, every element appears twice except for one. Find that single one.
Native approach is using freq table or hashtable with take O(n) space.
Best approach is xor of all number because x^x = 0 and a^b=b^a So, we can twice number eliminate themselves. The left number is our ans

```
  public int singleNumber(final List<Integer> A) {
        int ans=0;
        for(int a:A)
            ans^=a;
        return ans;
    }

```
### Signed Right Shift
When we shift any number to the right, 
its handle the most significant position (leftmost) in two different ways If number is -ve it filled with the msb sign('1') bit to maintain the negivity of that number 
e.g = -2>>1 = 111..10 >> 1 === 111....111 = -1 So, -2>>1 = -1 
and it fills 0 if number is +ve eg: 3>>1 = 000...011 >> 1 = 0000...001 === 1.

### Unsigned Right Shift ('>>>')
When we shift any number to the right, the vacant leftmost position is filled with 0 always.

### Right Shift and Left Shift
Right shift of any no means dividing that number by 2 and Left shift of any number means multiplying by 2

**Note** All this dividing and multiplying are for smaller shift number or smaller integer. Larger integer leads overflow of that number 

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

### Get Quotent and Remainder for power of 2 e.g-2,4,8,16,... 
Hey everyone!! as we all know playing with bit-manupulation is like magic. Today i learn about one of the magic i.e
If we divide anything with power of 2 (e.g :- 2,4,8,16,32....) we can calcuate remainder and quotent in 1s.
Lemme tell u how ? 

1st : for e.g => n=15 (1111) <br/>
15/2 = 7(quotent), 1(remainder)<br/>
![image](https://user-images.githubusercontent.com/54256549/153720795-14b7c44e-3237-47a1-b86f-96d7cbf660cf.png)

//-arly for 8,32,64,128
