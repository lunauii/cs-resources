# Quiz 1: Foundations

- Define "object" **(1/12)**

- What is wrong with the following code? Explain. Fix it. **(1/12)**

```java
if (s.isBlank() || s == null)
{
    throw new IllegalArgumentException("no string!");
}
```

**Solution**: If `s` is null, it won't have the `isBlank` method. Fix: `if (s==null || s.isBlank())`

- Create a Main class with the `main()` method and print out the third argument. **(2/12)**

**Solution**:

```java
public class Main
{
    public static void main(final String[] args)
    {
        System.out.println(args[2]);
    }
}
```

- What does `final` mean? ive an example of a field that should be final for a Person class. **(2/12)**

**Solution**: Means the variable can only be assigned once. It's a compile error if you try to assign it the 2nd time. Example: a Person's date of birth.

- Create a Restaurant class with two well-named instance variables: nationality (e.g. Italian), opening and closing hours (use a 24-hour clock), getters and setters as appropriate, and a constructor. With JavaDoc comments. Use proper validation techniques.
