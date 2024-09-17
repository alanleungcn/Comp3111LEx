# Lab 2

- LEUNG, Cheuk Nang
- 20949965

## Lab2b

```java
package Lab2b;

/*	Comp3111LEx\Lab2b\Book.java		*/
public class Book {
    private String chapters[];
    private static final int DEFAULT_CHAPTERS = 10;

    public Book() {
        chapters = new String[DEFAULT_CHAPTERS];
        for (int i = 0; i < chapters.length; i++)
            chapters[i] = "n/a";
    }
    public Book(String argument[]) {
        /* construct the object with an array of chapter names */
        /* PLEASE ADD YOUR CODE HERE */
        chapters = new String[argument.length];
        for (int i = 0; i < argument.length; i++)
            chapters[i] = argument[i];
    }
    public String getChapter(int i) {
        /* return the chapter by the given index */
        /* PLEASE ADD YOUR CODE HERE */
        return chapters[i];
    }
    public String[] getChapters() {
        return chapters;
    }
}
```

## Lab2c

`c.charge(m)` does not work originally because the `charge` method from the `Charger` class expects an object with `Chargeable` type, so that it can call the `charge` method within objects that implemented the `Chargeable` interface.

The fix is to add `implements Chargeable` for the `MobileComputer` class such that it implements the `Chargeable` interface and the `charge` method can be called.

```java
package Lab2c;

/*	Comp3111LEx\Lab2c\MobileComputer.java
	Inherits from Computer, class library for Lab2 Exercise 3	*/

public class MobileComputer extends Computer implements Chargeable {
    private int battery;
    public MobileComputer() {
        secret = "MobileComputer secret";
        battery = 5;
    }
    @Override
    public void work() {
        if (battery > 0) {
            System.out.println("It is working on my lap.");
            battery--;
        } else
            System.out.println("Running out of battery");
    }
    public void charge() {
        if (battery < 10)
            battery++;
    }
}
```