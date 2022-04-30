## Highest Common Factor / Greatest Common Divisor

1. They Both are same

#### Method to find GCD
##### 1. Native aprroach includes both iterative and recursice
```
while(i++>1) if(a%i==0 && b%i==0) gcd = i;
```
##### 2. Puzzle
  a. Draw a x b matrix 
  b. the highest square equal no of square you can form is gcd
  c. example a=100 nd b =200 the total 2 squares will from of size 100*100 Hence, gcd(100,200) = 100

##### 3. Euclidean Algorithm
  a. Normal
  
        ```
        Suppose gcd(a, b) = g(x, y), where g is natural number and gcd of a and b
        // x and y are pair those gcd will always one
        a = g(x)
        b = g(y)

        a-b = g(x-y)
        
        TC - O(max(a,b))
        ```
        
        ```
        static int gcd(int a, int b) {
        if (a == 0)
          return b;
        if (b == 0)
          return a;
      
        if (a == b)
            return a;
      
        // a is greater
        if (a > b)
            return gcd(a-b, b);
        // b is greater
        return gcd(a, b-a);
    }
        ```
      
  b. Optimal : we can reduce repeating subtraction by using '%' operator 
  
    ```
    static int gcd(int a, int b) {
      if (b == 0)
        return a;
      return gcd(b, a % b);
    }
    TC - O(log(max(a,b))
    Facts:  b is always smaller than a. even you pass b greater in first call it will swap automatically
    ```
