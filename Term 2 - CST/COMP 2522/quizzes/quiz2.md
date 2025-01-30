# Quiz 2: Inheritance \& Polymorphism

- Create a checked exception named `InvalidUsernameException`. Then create a `Login` class; `Login` has a `username` String variable and a `password` String variable. Its constructor must throw your new Exception if the username contains (in any letter casing) the word "admin". Then create a `Main` class: its main method creates a `Login` and prints its username and password. Show the best-practice way of doing this. **(6/12)**

- I created a class named `Rectangle` with an instance variables for `length` and `width`. Show its _default_ constructor; under what conditions is that constructor made by Java? Create a `Square` class that is a child of `Rectangle` too. **(2/12)**

- Create a class `Drink` with instance data for name (a String). Create a child class `CocaCola` that also has a boolean for whether it is "diet" or not. `Drink` has a method calld `display()` that prints its data. `CocaCola` overrides it and prints its data. **(4/12)**
