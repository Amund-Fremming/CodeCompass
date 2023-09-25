# Sorting Methods

**Bouble Sort**

- O(n^2)

**Selection Sort**

- O(n^2)
- Splits the array into a empty and a full array, searches for the smallest element in the populated array then puts the element in the empty and does this til the array is sorted

**Insertion Sort**

- O(n^2)
- Splits the arrays into two arrays the first one containing only the first element, then we pick the first element of the second array and compares it to the first element in the array containing only one element. Inserts the element in the right spot

**Quick Sort**

- O(n^2)
- Splits the array in the center and takes out a partition, left side tries to find an element larger than pivot and the other side smaller than pivot, then they swap elements. When left side and right side meet the array is sorted
- The sorting and taking out pivot will happen recursivly

**Merge Sort**

- O(n logn)
- Splits the array into two, then does this all the way till the arrays only contain one element, then it starts to take one array and the other and sort them together, then continue this all the way back up again
