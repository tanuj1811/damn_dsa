# Subarray with given XOR
Very Imp.

Given an array of integers A and an integer B.

Find the total number of subarrays having bitwise XOR of all elements equals to B.

### Link: https://www.interviewbit.com/problems/subarray-with-given-xor/

```
  public class Solution {
    /**
        Approach is simple but difficult to memorize

        Suppose the subarray is giving xor is xr 
        e.g 4 2 2 6 i.e xr=2

        Suppose again, in the subarray which gives xor k
        2 2 6 gives xor =k
        let xor of remaining array is y
        So, we can say,
        y ^ k = xr
        xoring k on both
        y ^ k ^k = xr ^ k

        y=xr ^ k

        map is for how many times y already come
        4->4
        4^ 2^ 2 -> 4
        

    */
    public int solve(ArrayList<Integer> A, int k) {
       int count=0;
       int xr=0; // current xor
       HashMap<Integer,Integer> map=new HashMap<>(); //stores y wrt count
       //y=xr^k
       for(int a:A) {
            xr^=a;
            if(map.containsKey(xr^k)) //y=xr ^ k
                count+=map.get(xr^k);
            if(xr==k) count++;

            map.put(xr,map.getOrDefault(xr,0)+1);

       }
       return count;
    }
}

```
