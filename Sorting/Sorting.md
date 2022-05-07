# Sorting

#### Stable Sort : 
A Stable Sort is one which preserves the original order of input set,
where the comparison algorithm does not distinguish between two or more items. 
A Stable Sort will guarantee that the original order of data having the same rank is preserved in the output.

Example: 
```
array s = [{name: "xyz", marks: 50}, {name: "sharma", marks: 100}, {name: "tanuj", marks: 100}]

sort(s, (a,b) -> Integer.compare(a.marks,b.marks);
O/P : [{name: "sharma", marks: 100}, {name: "tanuj", marks: 100}, {name: "xyz", marks: 50}]

Note: while sorting it take care the order of given input if two marks are same its focus on given order,
sharma is printed first in the given example
```

**Sotring Algo's like : Insertion Sort, Merge Sort, Bubble Sort, Tim Sort are stable sorting algo's**

#### Unstable Sort : 
In an unstable sorting algorithm the ordering of the same values is not necessarily preserved after sorting.

![image](https://user-images.githubusercontent.com/54256549/167083957-1c6ed0b3-e25e-4f91-ad3b-639e9652817a.png)


**Sotring Algo's like :Heap sort, Selection sort, Quick sort are stable sorting algo's**

#### In-place Sort : the sorting algo which doesn't occupy any extra memory.

## Bubble Sort
It compares two adjacent elements and swaps them until they are not in the intended order.

Just like the movement of air bubbles in the water that rise up to the surface,
each element of the array move to the end in each iteration. Therefore, it is called a bubble sort.

At every iteration largest element is placed at the end

Stability - Stable
TC - O(n<sup>2</sup>) // worst case
SC - O(1)

```
public void bubbleSort(Object[] a) {
  int size =a.length;
  for (int i = 0; i < size - 1; i++) {
     for (int j = 0; j < size - i - 1; j++) {
       if (array[j] > array[j + 1]) {
          // swapping occurs if elements
          int temp = array[j];
          array[j] = array[j + 1];
          array[j + 1] = temp;
       }
     }
  }
}
```

## Selection Sort
Itis an in-place comparison-based algorithm in which the list is divided into two parts, the sorted part at the left end and the unsorted part at the right end. Initially, the sorted part is empty and the unsorted part is the entire list.

The smallest element is selected from the unsorted array and swapped with the leftmost element, and that element becomes a part of the sorted array. This process continues moving unsorted array boundary by one element to the right.

![image](https://user-images.githubusercontent.com/54256549/167095347-11a9d202-3911-4c8d-af44-32b9afa43dc5.png)

Stability - Unstable
TC - O(n<sup>2</sup>) // worst and avg case
SC - O(1)

```
public void selectionSort(Object[] a) {
  int n = a.length;
  int min=0;
  for(int i=0;i<n-1;i++) {
    min=i;
    for(int j=i+1;j<n;j++) {
      if(a[min]>a[j]) min=j;
    }
    swap(a,i,min);
  }
}
```
## Tim Sort :
its a hybrid algo means it's sort array using merge sort and insertion sort.

Insertion sort is used when size is small or become small

Stability - Stable
TC - O(nlog n) // worst case

## Insertion Sort
It is most used and most popular for small size array. 

Stability - Stable
TC - O(n<sup>2</sup>) // worst case
Sc - O(1)

```
public void insertioSort(int[] a) {
  int n = a.length;
  int min;
  for(int i=1;i<n;i++) {
    int key = a[i];
    int j=i-1;
    while(j>=0 && key<a[j]) {
      a[j+1]=a[j]; // shifting elements to the right side to insert key
      j--;
    }
    a[j+1]=key;
      
    arrci+1]=ai[3]; 
  }
}
```

## Quick Sort
https://github.com/tanuj1811/DSA-Memorization/blob/main/Quick%20Sort%20and%20Partition.md

# Problems

## Count Inversion - Imp.
Given an array of integers. Find the Inversion Count in the array. 

**Inversion Count**: For an array, inversion count indicates how far (or close) the array is from being sorted. If array is already sorted then the inversion count is 0. If an array is sorted in the reverse order then the inversion count is the maximum. 
Formally, two elements a[i] and a[j] form an inversion if a[i] > a[j] and i < j.

```
public int inversionCount(int[] a) {
  return mergeSort(a);
}

public int mergeSort(int[] a) {
    if(l>=r) return 0;
    
    int mid = (l+r)>>1;
    return mergeSort(a,l,mid) + mergeSort(a,mid+1,r) + merge(a,l,mid+1,r);
}

public int merge(int arr[], int start, int mid, int end) {

  int inversions = 0, i = start, j = mid, k = 0;
	int temp[end - start + 1];

	while(i < mid && j <= end){ 
		if(arr[i] <= arr[j])
			temp[k++] = arr[i++];
		else {
			temp[k++] = arr[j++];
			inversions += mid - i; // this count the inversion
		}
	}

	while(i < mid) 
		temp[k++] = arr[i++];

	while(j <= end) 
		temp[k++] = arr[j++];

	for(i = start; i <= end; i++)
		arr[i] = temp[i - start];
		
	return inversions;
}
```


