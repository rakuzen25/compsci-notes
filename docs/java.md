# Java Cheatsheet

!!! note
    Uninitialised local variables in Java will cause a **compile error**, while uninitialised class variables (fields) will be initialised to a **default value** of `null` (if reference type) or `0` (if primitive type).

```java
public class Test {
    int a;
    public static void main(String[] args) {
        int b;
        System.out.println(a); // 0
        System.out.println(b); // Compile error
    }
}
```

## Boilerplate

!!! warning "Attention"
    The class name must be identical to the file name.

```java
public class className {
    public static void main(String[] args) {
        // Some code
    }
}
```

## Output

```java
// Print with newline
System.out.println("Hello World!");

// Print without newline
System.out.print("Hello ");
System.out.print("World!\n");
```

## Input

```java
import java.util.Scanner;

// in main
Scanner sc = new Scanner(System.in);
String input = sc.nextLine();
```

Be careful: `nextInt()` does not read a newline character, so if `nextLine()` is used directly after, it will only read a newline character. See [this SO answer](https://stackoverflow.com/a/13102066).

```java hl_lines="2"
int a = sc.nextInt();
sc.nextLine();
String b = sc.nextLine();
```

## File handling

```java
import java.io.*;
import java.util.Scanner;

// in main
// Read from file
try {
    File file = new File("filename.txt");
    Scanner sc = new Scanner(file);
    while (sc.hasNextLine()) {
        String line = sc.nextLine();
        // Do something with line
    }
    sc.close();
} catch (FileNotFoundException e) {
    System.out.println("An error occurred.");
}

// Write to file
try {
    FileWriter file = new FileWriter("filename.txt");
    file.write("Hello World!");
    // Write with new line
    file.write("Hello World!" + System.lineSeparator());
    file.close();
} catch (IOException e) {
    System.out.println("An error occurred.");
}
```

## Math

!!! Note
    `Math` is from `java.lang.Math`, which is imported by default.

### Min/Max

```java
int min = Math.min(a, b);
int max = Math.max(a, b);
```

### Random

```java
// This gives a random number in the range of [min, max)
int rand = min + (int)(Math.random() * (max - min));
```

## Array

See [HL01](HL/01.md).

## ArrayList

The equivalent of `vector` in C++ (a dynamic array).

!!! warning "Attention"
    `ArrayList` **cannot** accept primitive types (e.g. `int`, `double`), so a class must be used instead (e.g. `Integer`, `Double`).

```java
import java.util.ArrayList;

// in main
ArrayList<Integer> arr = new ArrayList<Integer>();

// 2D ArrayList
ArrayList<ArrayList<Integer>> arr = new ArrayList<ArrayList<Integer>>();
// alternatively, use the diamond operator
ArrayList<ArrayList<Integer>> arr = new ArrayList<>();
```

### ArrayList methods

```java
// Add to end
arr.add(element);

// Insert at index
arr.add(index, element);

// Replace at index
arr.set(index, element);

// Get element
int a = arr.get(index);

// Remove element
arr.remove(index);
arr.remove(element);

// Get size
int size = arr.size();

// Clear
arr.clear();

// Check if empty
boolean empty = arr.isEmpty();

// Check if contains element
boolean contains = arr.contains(element);

// Get index
int index = arr.indexOf(element);

// To array
Integer[] arr2 = arr.toArray(new Integer[arr.size()]);
```

```java
// Collections methods
import java.util.Collections;

// Sort
Collections.sort(arr);
// Sort in reverse
Collections.sort(arr, Collections.reverseOrder());
// Sort with custom comparator
Collections.sort(arr, new Comparator<Integer>() {
    @Override
    public int compare(Integer a, Integer b) {
        return a - b;
    }
});

// Reverse
Collections.reverse(arr);

// Shuffle
Collections.shuffle(arr);

// Swap
Collections.swap(arr, i, j);

// Rotate
Collections.rotate(arr, distance);

// Fill
Collections.fill(arr, element);

// Replace all
Collections.replaceAll(arr, oldElement, newElement);

// Frequency
int freq = Collections.frequency(arr, element);

// Max
int max = Collections.max(arr);

// Min
int min = Collections.min(arr);

// Binary search
int index = Collections.binarySearch(arr, element);

// Add all
Collections.addAll(arr, element1, element2, ...);
```
