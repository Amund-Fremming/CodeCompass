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
