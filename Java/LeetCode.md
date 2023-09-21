**Reverse array of characters just by modifying the array**

```java
public void reverseString(char[] s) {
    int left = 0;
    int right = s.length - 1;

    while(left < right) {
        char temp = s[left];
        s[left] = s[right];
        s[right] = temp;

        left++;
        right--;
    }
}
```

**Find out if a number is prime number**

```java
public static boolean isPrime(int num) {
    if (num <= 1) {
        return false;
    }
    for (int i = 2; i <= Math.sqrt(num); i++) {
        if (num % i == 0) {
            return false;
        }
    }
    return true;
}
```

**Given two arrays in non-dec, and length m and n, arr1 has size m+n, sort them togehter in array 1. Empty spots in array1 has value 0**

```java
public void merge(int[] nums1, int m, int[] nums2, int n) {
    int arr1 = m - 1;
    int arr2 = n - 1;
    int p = m + n - 1;

    while(arr1 >= 0 && arr2 >= 0) {
        if(nums1[arr1] > nums2[arr2]) {
            nums1[p] = nums1[arr1];
            arr1--;
            p--;
        } else {
            nums1[p] = nums2[arr2];
            arr2--;
            p--;
        }
    }

    while(arr2 >= 0) {
        nums1[p] = nums2[arr2];
        arr2--;
        p--;
    }
}
```

**one number array, and one num we dont want, remove all the val, edt the nums arr to be right and return num wrong**

```java
public int removeElement(int[] nums, int val) {
    // fjern alle elementer av val i nums
    // La tomrom være bakerst
    // Returner nummer elementer i val

    int i = 0;
    int j = 0;
    while(i < nums.length) {
        if(nums[i] != val) {
            nums[j] = nums[i];
            j++;
        }
        i++;
    }


    return j;
}
```
