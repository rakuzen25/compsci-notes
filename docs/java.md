# Java Notes

## Boilerplate

!!! attention
    The class name must be identical to the file name.

```java
public class className {
    public static void main(String[] args) {
        // Some code
    }
}
```

## Output

To print with a newline:

```java
System.out.println("Hello World!");
```

To print without a newline:

```java
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
int rand = min + (int)(Math.random() * (max - min));
```
