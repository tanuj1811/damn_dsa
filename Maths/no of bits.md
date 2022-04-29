## Number of digits in given number

find the number of digits in given number ?

### Method 
##### 1. Iterative and recurive 
```
while(n!=0):
      digit++
      n/=10;
```
```
if(n==0) return 0;
return 1+recFunc(n/10);

```

TC - O(d) : d = no of digits

SC - Iterative O(1) Recurisive O(d)

##### 2. Logrithmic Approach

``` 
return Math.floor(Math.log10(n))+1;
```
example: Log10(500) = 2.698 

Math.floor(Math.log10(500))+1 = 3

and mostly time comp. of Math.log10 is O(1)

