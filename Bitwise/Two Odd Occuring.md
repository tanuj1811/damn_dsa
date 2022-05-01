# Two Odd Occuring Element in Array
**Statement** Given an array which all element even number of times except 2 number

e.g : [1, 1, 2, 3, 3, 9, 9, 10, 10, 10] Here, 2 and 10 is occuring odd number of times
[1, 1, 2, 3, 3, 9, 9, 5] Here, 2 and 5 is occuring odd number of times


```

public int[] twooddoccruing(int[] ar) { // ar = [10, 20, 30, 20]
  //1. xor all number. 
  int xor=0;
  for(int a: ar) xor^=a;
 
  //xor will always eq to the xor of two odd occurance coz other will cancel out each other means xor = 10^30 = 1010^1110 = 0100 === 4
  
  // bone of ques is to get elements from xor i.e get 10 and 30 from 4
  
  // we know that if bits are different then only xor is 1. So, we gonna find least significant set bit from xor.
  int leastSignificantBit = xor&(~(xor-1)); //rightmost set bit // from bellow img understandable is easy
  
  
  // now we gonna two group. Groups 1 that have leastSignificantBit is set and Groups 2 that have leastSignificantBit is 0 .
  // and then xor all number in group 1 and after that we will get 1 of our answer element and xor of group 2 will give 2nd element 
  int xorGroup1=0, xorGroup2=0 ;
  for(int a: ar) {
    if((a & leastSignificantBit)!=0) xorGroup1^=a;
    else xorGroup2^=a;
  }
  
  return new int[] {xorGroup1, xorGroup2};
}


```
![image](https://user-images.githubusercontent.com/54256549/166143981-de840c66-f9d3-4eec-a598-4b80a28e3aef.png)


