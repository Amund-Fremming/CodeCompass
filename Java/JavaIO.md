# Java Input/Output system

**_Lese fra en fil_**

```java
try (BufferedReader br = new BufferedReader(new FileReader("filnavn.txt"))) {
    String line;
    while ((line = br.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```

**_Skrive til en fil med BufferedWriter_**

```java
try (BufferedWriter bw = new BufferedWriter(new FileWriter("filnavn.txt"))) {
    bw.write("Dette er en tekstlinje.");
    bw.newLine();
    bw.write("Dette er en annen tekstlinje.");
} catch (IOException e) {
    e.printStackTrace();
}
```
