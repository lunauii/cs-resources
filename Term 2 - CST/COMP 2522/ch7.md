---
author:
    - name: lunauii
      avatar: "https://avatars.githubusercontent.com/u/65362444?s=48&v=4"
icon: rocket
label: 'Lesson 7: Functional Interfaces, Lambda Expressions, Method References'
---

# Lesson 7: Functional Interfaces, Lambda Expressions, Method References

## Topics Covered

- Functional Interfaces
- Lambda Expressions
- Method References

!!! All of these only available after JRE/JDK 8.
!!!

## Functional Interfaces

An interface which only has a **single** abstract method. Can have default and static methods.

Can declare with `@FunctionalInterface` (optional, but highly recommended for clarity)

Java automatically knows what types, parameters, and return type the interface implements due to there only being one abstract method. Due to this, *`@Override` is not necessary* and it can be implemented just by using a **lambda expression**.

See Java interface `Consumer<T>`.




## Lambda Expressions

## Method References

Method references are a *shorthand syntax* which can *replace* lambda expressions.

Method references use the `::` operator without any parameters.

!!!info
``Class::staticMethod`` is an alternative to the lambda expression `(args) -> Class.staticMethod(args)`.
!!!

- Can be used to make simple lambda expressions by making use of existing methods
- Should be used over lambda expressions when there are more complex/repetitive tasks

```java
/*
 * Given an ArrayList<String> called names...
 */

// Example 1
names.forEach(System.out::println);

// Example 2; given methods in School
names.forEach(School::printStrLen);
names.forEach(School::printReverse);

```

Notice the `::` in the examples.