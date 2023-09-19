# JUnit Testing

**_Annotations_**

- @Test: before a test method
- @Before: runs before each test, good to be used as a data filling method

**_Asserts_**

- assertEquals()
- assertTrue()

**_Test Class_**

```java
public class ArrayTest {

    private int[] numbers;

    @BeforeEach
    public void setup() {
        numbers = new int[]{1, 2, 3, 4, 5, 6, 7, 8, 9};
    }

    @Test
    public void testLastNumberIsNine() {
        int lastNumber = numbers[numbers.length - 1];
        assertTrue(lastNumber == 9, "The last number should be 9");
    }

    @Test
    public void testArrayLength() {
        int expectedLength = 9;
        assertEquals(expectedLength, numbers.length, "The array length should be 9");
    }
}
```
