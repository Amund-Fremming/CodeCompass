## Checkliste før kode

- Må parameter modifiseres eller kan vi lage ny
- Mulig å iterere bakover spesielt om noe skal fylles opp
- .trim(\\s+) fjerner alt whitepsace
- Bruke to pekere? en som leter og en som står på plass som skal fjernes

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

**Fjern duplikater i en array og returner antall duplikater og la arrayen ha alle stigende tall i rekkefølge uten duplikater i arrayen**

```java
public int removeDuplicates(int[] nums) {
    int j = 1;
    for(int i = 1; i < nums.length; i++) {
        if(nums[i] != nums[i - 1]) {
            nums[j] = nums[i];
            j++;
        }
    }

    return j;
    }
```

**Flytt en array k ganger mot høyre**

```java
public void rotate(int[] nums, int k) {
    k %= nums.length;
    reverse(nums, 0, nums.length - 1);
    reverse(nums, 0, k-1);
    reverse(nums, k, nums.length - 1);
}

public void reverse(int[] nums, int start, int end) {
    while(start < end) {
        int temp = nums[start];
        nums[start] = nums[end];
        nums[end] = temp;
        start++;
        end--;
    }
}
```

**Gitt en array med priser, der i representerer dagen, finn maksimal profit**

```java
public int maxProfit(int[] prices) {
    int bestProfit = 0;
    int lowest = Integer.MAX_VALUE;
    int profitNow = 0;

    for(int i = 0; i < prices.length; i++) {
        if(prices[i] < lowest)
            lowest = prices[i];

        profitNow = prices[i] - lowest;
        if(profitNow > bestProfit)
            bestProfit = profitNow;
    }

    return bestProfit;
}
```

**En arrray med tall, tallene viser hvor langt du kan maksimalt hoppe, målet er å nå siste index**

```java
public boolean canJump(int[] nums) {
    int reach = 0;
    for(int i = null; i < nums.length; i++) {
        // Vi har gått for langt
        if(i > reach) return false;

        // Lagrer ny reach om vi har ett lenger der vi stå rnå, eller om den gamle rekkevidden fortsatt er lengre
        reach = Math.max(reach, i + nums[i]);
    }
    return true;
}
```

**Merge two strings, alternating from left**

- Bruk stringbuilder men ikke string og legg til på den

```java
class Solution {
    public String mergeAlternately(String word1, String word2) {

        StringBuilder builder = new StringBuilder();
        int len = word1.length() > word2.length() ? word1.length() : word2.length();

        for(int i = 0; i < len; i++) {
            if(i < word1.length()) {
                builder.append(word1.charAt(i));
            }

            if(i < word2.length()) {
                builder.append(word2.charAt(i));
            }
        }

        return builder.toString();
    }
}
```

**Finnes det tre tall i en araray der arr[i] < arr[j] < arr[k] og i < j < k**

```java
public boolean increasingTriplet(int[] nums) {
    int pointer1 = Integer.MAX_VALUE;
    int pointer2 = Integer.MAX_VALUE;
    for(int i = 0; i < nums.length; i++) {
        if(nums[i] <= pointer1) {
            pointer1 = nums[i];
        } else if(nums[i] <= pointer2) {
            pointer2 = nums[i];
        } else {
            return true;
        }
    }

    return false;
}
```

**Gitt en array med stolper, hva er maksimal mengde vann vi kan holde**

```java
public int maxArea(int[] height) {
    int biggestVol = 0;
    int left = 0;
    int right = height.length - 1;

    while(left < right) {

        int minHeight = Math.min(height[left], height[right]);
        biggestVol = Math.max(biggestVol, minHeight * (right-left));

        if(height[left] < height[right])
            left++;
        else
            right--;
    }

    return biggestVol;
}
```

**Finn sub array med lengde k som har størst average**

```java
public double findMaxAverage(int[] nums, int k) {
    double sum = 0.0;
    for (int i = 0; i < k; i++) {
        sum += nums[i];
    }

    double maxSum = sum;
    for (int i = k; i < nums.length; i++) {
        sum += nums[i] - nums[i - k];
        maxSum = Math.max(maxSum, sum);
    }

    return maxSum / k;
}
```

**Finn størst antall vokaler i en substring med lengde k, i en string**

```java
public int maxVowels(String s, int k) {
    char[] arr = s.toCharArray();
    int maxVowels = 0;

    //Initial Window
    for(int i = 0; i < k; i++) {
        if(isVowel(arr[i])) {
            maxVowels++;
        }
    }

    int localVowels = maxVowels;
    // Slide the Window
    for(int i = k; i < arr.length; i++) {
        // skal vekk fra vindu
        if(isVowel(arr[i - k]))
            localVowels--;

        // skal inn i vindu
        if(isVowel(arr[i]))
            localVowels++;

        maxVowels = Math.max(maxVowels, localVowels);
    }

    return maxVowels;
}

boolean isVowel(char c) {
    return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
}
```

**Er stringen med paranteser balansert?**

```java
public static boolean balanceParenthesis(String s) {
    public boolean isValid(String s) {
    Deque<Character> stack = new ArrayDeque<>();
    for(char c : s.toCharArray()) {
        if(c == '(')
            stack.push(')');
        else if(c == '[')
            stack.push(']');
        else if(c == '{')
            stack.push('}');
        else if(stack.isEmpty() || stack.pop() != c)
            return false;
    }

    return stack.isEmpty();
}
```

**Snu lenket liste**

```java
public static void reverse(Node head) {
    // snu alle pekere
    // sett neste til neste
    // sett nodens neste til forrige, snu peker
    // sett forrige til denne
    // set denne til neste

    Node prev = null;
    Node current = head;
    Node next = null;

    while(current != null) {
        next = current.next;
        current.next = prev;
        prev = current;
        current = next;
    }

    }
```

**Hvordan finne midtren av en lenketliste**

```java
public static Node findCenterRek(Node head) {
    // En som går en om gangen, den andre går to, når andre er i slutten er vi framme med sakt
    if(head == null) return null;

    Node slow = head;
    Node fast = head;

    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }

    return slow;´
}
```

**Finn høyde av ett tre**

```java
public static int findTreeHeight(TreeNode root) {
    // Hvert tre må spørre hva høyden til treet under og plusse på 1 for seg selv
    // dette går rekursivt ned til vi er tomme og deretter returneres 1 + høyden til treet hele veien opp
    if(root == null) return 0;

    int leftHeight = findTreeHeight(root.left);
    int rightHeight = findTreeHeight(root.right);

    return 1 + Math.max(leftHeight, rightHeight);
}
```

**Reverseer ett binærtre**

```java
public static void reverseBinaryTree(TreeNode root) {
    // Starter på topp, hvis denne er null reture (Base case)
    // bytt venstre og høyre tre
    // rekursivt speil venstre tre og høyre tre
    if(root == null) return;

    TreeNode temp = root.left;
    root.left = root.right;
    root.right = temp;

    reverseBinaryTree(root.left);
    reverseBinaryTree(root.right);
}
```

**Sortering**

```java
public static void selectionSort(int[] arr) {
    int n = arr.length;

    for(int i = 0; i < n-1; i++) {
        int minste = i;
        for(int j = i+1; j < n; j++)
            // Finner minste
            if(arr[j] < arr[i])
                minste = j;


        int temp = arr[minste];
        arr[minste] = arr[i];
        arr[i] = temp;
    }
}

public static void insertionSort(int[] arr) {
    int n = arr.length;

    for(int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;

        while(j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }

        arr[j + 1] = key;
    }
}

```

**Merge two linkedlists**

```java
public Node mergeTwoListst(Node list1, Node list2) {
    if(list1 != null && list2 != null) {
        if(list1.val < list2.val) {
            list1.next = mergeTwoLists(list.next, list2.next);
            return list1;
        } else {
            list1.next = mergeTwoLists(list1, list2.next);
            return list2;
        }
    }

    if(list1 == null) {
        return list2;
    }
}
```
