# Permutation and Combination in Programming

As we all know permutation and combination is used in subset or subsequence types of question where we find all subset with some condition.
So,
## where to use Permunation ?
#### General Use (n!) : 
  Its generally is to find total how many subset can be made from the array.
###### How it's works ? 
  It is easy if you iterate from backward.
  
  Last element of array have only 1 possible.=> 1
  
  2nd last element have 2 possible index to stay i.e n-1,n-2 => 2*1
  
  3rd last element have 3 possible index to stay i.e n-1,n-2,n-3 =>3*2*1 
  
and so on....


#### Number of Subset at the particular index : 
  Basic math if n! gives you no of all possible subset at index 0 to n.
  then i to n = (n-i)! 
  and 0 to i = (i)!
  
#### Number of Subset Possible of size K (imp.) (Order matters):

**_Note_ : Here Order matters means if array = a,b,c,d,e... and k = 2. Then the group formed will be like ab,ac,bc... 
Imp. thing is there is no subset like bc,ea.. The element occured first will be first in ans subset. 
**


If we want to calc number of subset in the array of given size lets say k.
  
In general, lets array be 1, 2, 3 , 4 ... 15 and k=3 Then,
Total Number of Subset Possible of size 3 = 15!/3!

In general :
**Total Number of Subset Possible of size k = n!/k!**
###### Let me tell you how ?
n! gives you total number of subset
k! given you total number of subset of size k which k*k-1*k-2 ... thats covers all possible subset of size less than k
So, after dividing its remove of subset of less than size k.


## where to use Combination ?
#### General Use (nCr) : 
  Its generally is to find total how many subset can be taken from subset wrt some condition.

#### Number of Subset Possible of size K (imp.) (Order doesn't matters): 
nCr
  

