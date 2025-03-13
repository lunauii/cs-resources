# Quiz 3: Abstract and Final

- Define and give clear Java example of each of the following terms:
    + Final method **(2/12)**
    + Final class **(2/12)**
    + Abstract method **(2/12)**
    + Abstract class **(2/12)**

**Solution**:

a\) A final method cannot be overrided by child classes. Make a method final when its implementation us critical to the class'es operation, so that child classes cannot mess it up.

Example:
```java
class Parent
{
    final void doSomething() {}
}

class Child extends Parent
{
    void doSomething() {} // COMPILE ERROR
}
```


b\) A final class cannot be extended/inherited. Make a class final when logically there's no further subtype of it.`

Example:
```java
final class IPhone16ProMax
{
    // This class is final because there's no subtype of this iPhone.
}

class Something extends IPhone16ProMax {} // COMPILE ERROR
```

c\) **MISSING**

d\) An abstract class cannot be instantiated. You must extend the class in order to create instances. An abstract class may, but doesn't have to, contain abstract methods.

Example:
```java
abstract class IDevice() {}

IDevice device =  new IDevice(); // COMPILE ERROR
```

Use abstract class when you want to factor out common code among other code in order to reduce code duplication, but the class itself doesn't make sense to be instantiated. For example, `IPhone` and `IPad` may have common code that can be reused, but "IDevice" is not a thing, so it shouldn't be instantiable.

- Create an IPhone class overrides `equals()` so that IPhones of the same version (e.g. 16) are "equal()". Show all the code. Use best practices (but commit JavaDoc comments) **(4/12)

**Solution**: *I don't have one, but remember that whenever you override equal(), you must override hashCode() as well.*