**Reverse a sorted list**

```java
LinearNode<T> r, n, s;
s = start;
r = null;
while(s != null) {
    n = s;
    s = s.getNext();
    n.setNext(r);
    r = n;
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
