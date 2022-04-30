## Computing Power

Compute the x<sup>n</sup>
```

int ret = 1;
while(n!=0) {
  x*=x;
  if((int)(n&1)!=0) ret=ret;
  n>>=1;
}
System.out.println(ret);
```

### Explaination
![image](https://user-images.githubusercontent.com/54256549/166103998-ae864d20-4116-4ec9-b887-deabd38226ca.png)
