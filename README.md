# java-core-notes
Java Core Notes

## When you make things faster it will make you slower

## Understand the concept, rather than memorizing the code

# Java
- Is a high level compilef programming languange known for its strong security features, extensive in built libraries, and platform independent that been developed by James Gosling and his team at sun microsystem that has first name of Oak and later been named Java based on a coffee in indonesia. That very famous for "Write Once, Run Anywhere" qoute that has JVM.

# Java Virtual Machine
- Is responsible for executing java byte-code, which is a compiled form of java code. And also responsible for handling garbage collection that allocated amd deallocates memory dynamically.

# OOP (Object Oriented Programming)
- Meaning is organize the structure of the code thats mimics real world objects via software objects that has their own behavior and properties. And has 4 Pillars of Inheritance, Polymorphism, Encapsulation, and Abstraction.

# Why java is not fully Object-oriented
- Bacause of primitive types byte, short, int, long, float, and double.

# Java naming conventions
- **Classes** should be noun, always capital letter for each word, and should match to the file name.
```
Foo✅ file name should be Foo.java
FooBar✅ file name should be FooBar.java
```
- **Method** should be verb and use camel casing.
```
Foo foo = new Foo();
foo.greet()✅
foo.greetBar()✅
```
- **Variable** should be noun and use camel casing.
```
String foo;✅
int bar;✅
```
- **Constant Variable** should be in snake case, always have value when declared, and all caps.
```
float PI = 3.14;✅
int DEFAULT_VALUE = 1;✅
```
##### Note: by writing code base on naming conventions it will make your code readable, able to follow enterprise quality code and when you reading code you can identify amd differentiate right away what is function, variable, and class. 

# Access modifiers
- **public**: can be used anywhere in the program
- **protected**: can only be used by child class and not avaiable globally.
- **private**: only available inside the specific class it was declared on
- **package-private**: the default access modifier that only available in the specific package it was declared on.
##### Note: In inheritance access modifier cannot be more restricted than the declared one. for example

# Non-access modifiers
- **final**: use to declare a constant variable, prevent method to be overwritten and also prevent other class to be able extend in class.
- **static**: is used to the variable and method, class that are not really binded in encapsulating class.
- ##### When to use static keyword? for me concrete object should not contain static methods or fields it should be in separate helper or utility class that should only contains static methods and fields for that class. because its awkward to say example ypu have code of
```
Foo foo = new Foo();
foo.getTotalFoo(); // static method in Foo class

instead

FooHelper.getTotalFoo(); // are much more readable and concise
```
##### Note: static methods and variables should be access via the class itself instead of object instance.
```
bar() // is the static method
Foo.bar()✅

Foo foo = new Foo();
foo.bar()❎
```

# Variable scoping 
- **Global variable**: declared in encapsulating class that accesible anywhere in the class.
- **Local variable**: declared usually inside the method and only accessible within that method.
```
public class Foo {
  private String bar; // Global scope available anywhere in this class
  public void greetBar() {
    String foo; // Local scope only available inside this method
  } 
}
```
##### Note: Scoping of methods and variable in java are always only within the curly brackets {} it was declared on 

# What is class
- Class acts like a blueprint to create an object that has properties = fields and behavior = methods.

# Difference of this and super keyword
- **this**: is used to reference the methods and fields of current object.
```
public class Foo {
  private String bar;
  public void Foo(String bar) {
    this.bar = bar;
    // here the this keyword contains the current class methods and variables that you can access.
  }
}
```
- **super**: used to reference the methods and fields of super class.
```
public class Foo {
  public void greet() {
  // Code here
  }
}

public class Bar extends Foo {
  @Override
  public void greet() {
    super.greet();
    // Here super keyword is used to call the super class method
  }
}
```

# When to use inheritance
- If there are common fields and methods in a parent class and child class.
- If your classes has a relation and their relation can be read both as is-a or can-be for example:
  - Car is a ElectricCar
  - Car can be ElectricCar

# When to use interfaces
- When you need multiple inheritance because java doesn't allow multiple inheritance.
- If your classes needs a contract that they can do the methods that are declared in interface.

# Difference of == operator and equals() method
- Double equals only check if two objects memory location are the same.
- equals() method check not the memory location but the content of the object.

# Definition of Terms
- Implicit = Automatic
- Explicit = Manual
- Sub class, Derived class and Child class are all the same.
- Super class, Base class and Parent class are all the same.
- Method, Function, and Behavior are all the same.
- Field, Property, Variable are all the same.
