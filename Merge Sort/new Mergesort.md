Okay let me try to explain the thought process behind this code.
Prerequisite: number of inversions {A[i] > A[j] : i < j} can be counted during the merge step of merge sort.

So we start with the standard merge code (Refer any algorithm book like CLRS etc):

```
  void merge(int[] A, int l, int m, int r, int[] M) {
	int i = l, j = m + 1, k = 0;
	while(i <= m && j <= r) {
		M[k++] = A[i] <= A[j] : A[i++] : A[j++];
	}
	while(i <= m) {
		M[k++] = A[i++];
	}
	while(j <= r) {
		M[k++] = A[j++];
	}
	for(i = l; i <= r; i++) {
		A[i] = M[i - l];
	}
}

```
We can achieve the same goal by tweaking the first while loop into a for loop like this (this makes the inversions counting part cleaner as we'll see in a sec):
```
void merge(int[] A, int l, int m, int r, int[] M) {
	int i = l, k = 0;
	for(int j = m + 1; j <= r; j++) {
		while(i <= m && A[i] <= A[j]) {
			M[k++] = A[i++];
		}
		M[k++] = A[j];
	}
	while(i <= m) {
		M[k++] = A[i++];
	}
	for(i = l; i <= r; i++) {
		A[i] = M[i - l];
	}
}
```
Add the logic to count inversions:
```
int merge(int[] A, int l, int m, int r, int[] M) {
	int i = l, k = 0, res = 0;
	for(int j = m + 1; j <= r; j++) {
		while(i <= m && A[i] <= A[j]) {
			M[k++] = A[i++];
		}
		res += m - i + 1;
		M[k++] = A[j];
	}
	while(i <= m) {
		M[k++] = A[i++];
	}
	for(i = l; i <= r; i++) {
		A[i] = M[i - l];
	}
	return res;
}
```
In this problem, however, the definition of inversion is slightly changed so we can't use i and need to introduce another variable t to iterate on left half (similar to i):
note 1: iterating on left half twice (because of introducing t) doesn't change the worst case time complexity
note 2: 2L * A[j] is a subtle way to force this calculation into long thereby avoiding incorrect results
```
int merge(int[] A, int l, int m, int r, int[] M) {
	int i = l, t = l, k = 0, res = 0;
	for(int j = m + 1; j <= r; j++) {
		while(t <= m && A[t] <= 2L * A[j]) {
			t++;
		}
		res += m - t + 1;
		while(i <= m && A[i] <= A[j]) {
			M[k++] = A[i++];
		}
		M[k++] = A[j];
	}
	while(i <= m) {
		M[k++] = A[i++];
	}
	for(i = l; i <= r; i++) {
		A[i] = M[i - l];
	}
	return res;
}
```
