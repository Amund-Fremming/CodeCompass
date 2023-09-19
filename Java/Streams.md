# Lamda and Streams

**_Lamda Expression_**

- Predicate<T> boolean
- Consumer<T> Singel input, no return
- Funciton<T, R> Single input, single return
- Supplier<T> no arguments only return
- BiFunction<T, U, R> Two inputs, single return
- BiPredicate<T, U> Two bool input, one out (equals)
- BiConsumer<T, U> Two inputs, no return

```java
Comparator<String> stringLengthComp = (s1, s2) -> s1.length() - s2.length();
```

**_Streams_**

- filer
- map
- flatMap(Function<T, Stream<R>> mapper)
- distinct
- sorted
- sorted(Comparator<T> comparator)
- forEach
- toArray
- reduce(0, (a, b) -> a + b)
- min
- max
- count
- anyMatch
- noneMatch
- findFirst
- findAny
- Stream.of(...)
- For intStream, LongStream or DoubleStream use sum or average (use mapToInt)
