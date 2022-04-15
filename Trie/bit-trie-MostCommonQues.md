This is most common ques of bit-trie means most of bit-trie ques derived from this ques

![image](https://user-images.githubusercontent.com/54256549/163604926-2a4fa497-dfc1-4bad-a883-805f1b5f8828.png)


### Approach

1. Make the bit trie of 32 size. 32 because its signifies that at any i there will either 0 or 1
for e.g 7-> 111 so we wanna xor with suppose 16 -> 1000 it will show error .
So, we gonna store 7 and 16 as same as computer store 000000...111 and 00000..1000

2. Trie will look like tree
3. To maximize the xor. we will try to make every bit as 1 which is possible only when one of bit of x->i (bit at i-th index in x) and a[j]->i is 1 not both.
