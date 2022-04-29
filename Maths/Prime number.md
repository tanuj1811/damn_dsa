## Prime Number

those who have only 2 factors 1 or itself a number

example: 2, 3, 5, 7, 11

1. Every prime no can represent in the form of 6n+1 or 6n-1 except 2 and 3 // n is natural no
2. 2 and 3 are only consecutive prime number

### Method to wheathe n prime number or not

1. Native
```
for(int i=2->n) if(n%i==0) return n is not prime
```
TC - O(n) // worst case when n is prime no
2. Optimization

as we know, if n have factors then n is not prime. So,

let take x,y is factor of n
```
x*y = n
and x<=y
x*x<=n
x<=√n
```
So, Optimal Soln look like
```
if(n%2==0 || n%3==0) return n is not prime
for(int i=5;i*i<n;i+=6) { //i+=6 coz of 1 point above
  if(i%2==0 || i%3 == 0) continue; // to save time
  if(n%i==0) return n is not prime
  }

// TC-> O(less than √n )
```




#### Composite Number 
those who are not prime number
