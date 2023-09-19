# Concurrency

**_Threads_**

- Synchronized: this blocks other threads from using this part of the code
- wait: if a thread calls the wait the thread will stop its execution, and will wait here til notify method is called
- notify: Wakes up a single thread in the waiting pool
- notifyAll: Wakes up all the threads in the waiting pool

**_Synchronized code_**

```java
public class IncrementingThread extends Thread {
    private static int value = 0;  // Shared among all instances of this class

    // Synchronized increment method
    public synchronized void increment() {
        value++;
        System.out.println("Value after incrementing by " + Thread.currentThread().getName() + ": " + value);
    }

    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            increment();
            try {
                Thread.sleep(100);  // Optional: just to see the interleaving of threads more clearly
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }

    public static void main(String[] args) {
        IncrementingThread thread1 = new IncrementingThread();
        IncrementingThread thread2 = new IncrementingThread();

        thread1.start();
        thread2.start();
    }
}
```

**_Wait and notify_**

```java
public class SharedResource {
    private List<String> items = new ArrayList<>();

    public synchronized void produce(String item) {
        items.add(item);
        System.out.println("Produced: " + item);
        notify();  // Notify a waiting consumer that an item has been produced
    }

    public synchronized String consume() {
        while (items.isEmpty()) {
            try {
                wait();  // Wait until an item is produced
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        String item = items.remove(0);
        System.out.println("Consumed: " + item);
        return item;
    }
}
```
