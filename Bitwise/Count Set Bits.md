# Count Set Bits in given Integer

input 1: 11 = 000...01011
output: 3

input 2: 16
output :1


#### 1. Use Right shift util n become zero.
  ```
    while(n!=0) {
      if(n&1 == 1) setBit++;
      n=n>>1; // or n/=2;
    }
    
  ```
 TC-log(32) wrost case
 
we can reduce Time Complexity to O(setBit) by using 

#### 2. Kernighan's Algorithm

**__intution__**
```
  if we view binery representation of 2 consecutive number i.e
  
  816 = 1100110000
  815 = 1100101111
  814 = 1100101110
  
  Observation: all bits from left are same util last set bit and from last set bit all bits are reverse.
  
  we gonna use this to jump from least significant set bit to next less significant set bit in O(1) time.
  
```

```
while(n>0) {
  n = n & (n-1);
  setBit++;
}

```

we can futher reduce tc to O(1) by using extra memory or dp like data structure
#### 3. Look Up method to Set Bit
 
 Here we gonna compute set bits of all 2<sup>32</sup>-1 number store it in array.
 
 To do that we gonna divide 32 bits to 8 bits number which to 255
 
 ```
 int[] storage;
 public int initize() {
  storage = new int[256]
  for(int i=1;i<256;i++) {
    storage[i] = storage[i/2];
    if(i%2==1) storage[i]+=1;
  }
 }
 
 public void mainFunction() {
  int n = input();
  res= storage[n & 255]; // or storage[n & oxff] ff-> oxff is hexadecimal number for 7's 1's in binary
  n>>=8; //for next set of 8 bit 
  res+= storage[n & 255];
  n>>=8; //for next set of 8 bit 
  res+= storage[n & 255];
  n>>=8; //for next set of 8 bit 
  res+= storage[n & 255];
  
  System.out.println(res);
 }
 ```
 
 This initize function gives number of set bits of first 255 numbers correctly coz after every power of 2 number of set bit became to 1 
 
 2, 4, 16, 32, 64... all of those have number of set bit as 1
 
 
 
 
 
 
 
 
 
