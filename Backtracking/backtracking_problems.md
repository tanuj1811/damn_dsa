
*It's quite similiar to naive/brute force solution but in brute force you generate the case and then check it's leads to the answer or not while in backtracking you first check the condition*
In backtracking you mark/update the path you are going if some path doesn't lead to answer we undo the changes.


## Example of backtracking v/s brute force

Print all substring of the string "ABC" except substring who have "AB" as subsequence.

Brute force Solution
```
public void substring(String s) {
  substring(s,0,s.length());
}
public void substring(String s, int l, int r) {
  if(l==r) {
    if(!s.constains("AB")) System.out.println(s); //we are checking at the end just before printing
    return ;
  }
  for(int i=l;i<=r;i++) {
    swap(s,l,i);
    substring(s,l+1,r);
    swap(s,l,i);
  }
}
```

Backtracking Solution
```
public void substring(String s) {
  substring(s,0,s.length());
}
public void substring(String s, int l, int r) {
  if(l==r) {
    System.out.println(s);
    return ;
  }
  for(int i=l;i<=r;i++) {
    if(isSafe(s,l,i,r) { // checking if this path is leading to your answer
      swap(s,l,i);
      substring(s,l+1,r);
      swap(s,l,i);
    }
  }
}
public static boolean isSafe(String str,int l, int i, int r){
        if(l!=0 && str.charAt(l-1)=='A' && str.charAt(i)=='B')
            return false;
        if(r==(l+1) && str.charAt(i)=='A' && str.charAt(l)=='B')
            return false;
        return true;
    }
```

