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

### Find all prime factors of an number
We can achieve O(log n) for all composite numbers by consecutive dividing of the given number by an integer starting from 2 representing current factor of that number. This approach works on the fact that all composite numbers have factors in pairs other than 1 or number itself like 6=3 x 2 and 9=3 x 3

For example, We can divide 12 by 2 two times and remove that factors from 12 to get 3 thus making sure that composite number 4 (multiple of 2) does not occur at any later point of time.
and 

if we have a big number that is not divisible by any value of c=2 to n-1 means it is prime like 13 tc-> O(n)
 

```
  public static void primeFactors(int n) {
        int c = 2;
        while (n > 1) {
            if (n % c == 0) {
                System.out.print(c + " ");
                n /= c;
            }
            else
                c++;
        }
    }
```


### Composite Number 
those who are not prime number
