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
int fooBar;✅
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
##### Note: static methods and variables should be access via the class itself instead of object instance.
```
bar() // is the static method
Foo.bar()✅

Foo foo = new Foo();
foo.bar()❎
```
# When to use static keyword?
- For me concrete object should not contain static methods or fields it should be in separate helper or utility class that should only contains static methods and fields for that class. because its awkward to say example ypu have code of
```
Foo foo = new Foo();
foo.getTotalFoo(); // static method in Foo class

instead

FooHelper.getTotalFoo(); // are much more readable and concise
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

# Guard clause
- Guard clause is used to invert the logic and return early if the there was an validation triggered.
- Prevent nested if else
- When you use guard clause you will never use else statement in your life.
- Used with conjunction of throwing an error or return.
```
// old code
public void add(String name) {
  if (name.equals("bar")) {
     // Rest of the code
  } else {
     System.out.println("Your are not bar");
  }
}

// New code
public void add(String name) {
  if (!name.equals("bar")) {
    System.out.println("You are not bar");
    // Here we check immediately if hes bar and return or throw an error early.
    return;
    // throw new Exception
  }
  // Rest of the code
}
```

#### What are most prefer return or throw an error
- For me throwing an error are much more safer because you can ensure that rest of the code will not be executing if validation is triggered unlike return bugs can be lurking around if code continued executing after validation is triggered.

# What is class
- Class acts like a blueprint to create an object that has properties = fields and behavior = methods.

# What is abstract class and method
 ## Abstract Class
 - Used for not to create uncessary object
 - Abstract class cannot be instantiate or created
 ## Abstract Method
 - Abstract method is a method that has no implementation/body
 - Abstract method is meant to be overwritten.

# What is interface
- By default methods in interface are public and abstract
- By default fields in interface are public, final and static.
- Used when you need multiple inheritance.
- Used when you need just a contract that implementing class can do what method is declared in interface.
- Used when you dont need class heirarchy because interfaces bypass class heirarchy.
- Interface can have static methods and default methods

 ## Difference between static and default method in interface
 - They both need a body/implementatiom when declared in interface
  - **Default method**: Can be overwritten.
  - **Static method**: Cannot be overwritten.

# Inheritance
- Used to achieve polymorphism
- Inheritance is used if theres a common fields and methods to make code reusable and readable.
- Also if you want to have a relation between to classes to mimic real world objects.
```
public class Animal {
  private String name;
  public void eat() {}
}


public class Dog extends Animal {
  private String breed;
  public Dog(String name, String breed) {
    super(name);
    this.breed = breed;
  }

  @Override
  public void eat() {}
}
```
  ## Three types of inheritance
  - **Single level**: Class that extends in another class.
  - **Multi level**: Extending to a class that extends to another class
  - **Heirarchial**: The parent class has 1 or more child class.
![Inheritance](https://static.javatpoint.com/images/core/typesofinheritance.jpg)

##### Note: statics can be inherited but cannot be overwritten.

# Polymorphism
- Poly means many and morphism means many ways to represent.
  ## Two types of Polymorphism
 - **Static/ Compile time Polymorphism**: Achieved via method overloading meaning methods that have same name but return type, parameters types, and parameter ordering are not the same. Basically methods that only the same name are called method overloading.
```
public void m1() { }
public void m1(DataType arg1) { }
```
 - **Dynamic/ Runtime Polymorphism**: Achieved via method overriding meaning child class can do what is declared in parent class but has its own implementation or behavior.
```
public class Person {
  public void greet() { }
}

public class Student extends Person {
  @Override
   public void greet() {
     System.out.println("Student is greeting");
   }
}

public class Teacher extends Person {
  @Override
  public void greet() {
    System.out.println("Teacher is greeting");
  }
}

// As you can see student and teacher are extending in person class that has greet method but when they override that method thats it you have polymorphism and they are now have their behavior how to do greet.
```
##### Note: You cannot achieve method overriding without inheritance.

# Encapsulation 
- Implementation level
- Wrapping up the implementation data members and methods in a class. Used for data hiding.
  - You can achieve this by simply using getters and setters.
  - Usage of private and final keywords to hide and control what other class can access.

# Abstraction
- Design level
- Meaning hiding unecessary details and only showing valuable information.
- For example: When you have car and a key you start the car with the key and thats it the car works right away. But how does the key make the car starts this information we dont need to know but its important right thats how absttaction means hiding uncessary deatils and showing only valuable information.
- Example 2: There are two type of motor right manual that has clutch and automatic has only has accelerator and dont have clutch. Automatic abstracts the clutch that we dont need to manually manage the clutch instead automatically handling it behind the scenes that we dont to care about.

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
    super.greet(); // Will call the super class greet() method
    this.greet() // Will call the this current class greet() method
  }
}
```

# What does new keyword do and instatiate means?
- The new keyword is used to create = instatiate a new object based on the class you created as blueprint of the object.
```
Foo foo = new Foo();
// The new Foo() is the instantiation of the object.

// The Foo foo is the just the type and the variable name.
```

# Annotation
- Annotations is used to either add a metadata to a class, field, and method or Code documentation.
- Add metadata example
```
'@Retention'
'@Entity'
```
- Code Documentation
```
'@Override'
'@Depracated'
```
# Generics
- Used to have strong compiled time types and avoid type casting which commonly leads to bugs.
- Used when you need to a class, method, field that can work with different types. for example:
```
public interface Adder<T, U> {
 public void add(T t, U u) {
   System.out.println(t + u);
 }
}

// If you define a interface with different data type it will lead to class explosion instead use generics to have specific method can work with different types.
```
## Common generics naming convention
- Its naming convention in java that generics should have 1 letter name for readablity.

 - E = element
 - K = key
 - N = number
 - T = type
 - V = value
 - S = 2nd parameter
 - U = 3rd parameter
 - V = 4th parameter
 - R = return type
# Enums
- Used to represent a group of constant variables. Example: Deck of Cards, Months, and Genders.
```
public enum Gender {
 MALE,
 FEMALE
}
```

# How to construct a method or function
- Its important to deeply understand how to create and read a method because it will be useful when trying to debug and reading others code cause java is oop most of the time logics are written inside the methods. You will be able to make your code reusable and readable because you can break down big chunk of logic into separate methods.
```
// Method with void return type and no parameters
public void methodName() {

}
// public is the access modifier
// void is the return type
// methodName is the name of the method
// () is the parameters

// Method with return type and with parameters
public ReturnType methodName(DataType arg1, DataType arg2) {

}
// public is the access
// ReturnType is the return value of the method
// methodName is the name of the method
// (DataType arg1, DataType arg2) is the parameters
```
##### Note: 
  - void means nothing to return

# Difference between parameter and argument
- **Argument**: When you actually use or call the method and you supply the data inside the parameter is called argument.
- **Parameter**: When you declare a method inside () is called parameter.

##### Basically when you created a method is was called parameter and when you use that method it will be called as argument.

# When to use inheritance
- If there are common fields and methods in a parent class and child class.
- If your classes has a relation and their relation can be read both as is-a or can-be for example:
  - Car is a ElectricCar
  - Car can be ElectricCar

# When to use interfaces
- When you need multiple inheritance because java doesn't allow multiple inheritance.
- If your classes needs a contract that they can do the methods that are declared in interface.
- And their relation not really matters.
  
# Difference of == operator and equals() method
- Double equals only check if two objects memory location are the same.
- equals() method check not the memory location but the content of the object.
# Functional Interface
- Is an interface that has one and only one abstract method but can have any number of default and static method.
- Also used to create a lambda expression because this Functional Interface will become the type of the lambda expression this is where we will store our lambda expression
```
public interface MyFunctionalInterface {
  void m1() { }
}
```
# Lambda expression/Anonymous Functions
- Introduced in Java 8 that allows functional programming in java.
- Reduce boilerplate code
- Code optimization
- Used for data extraction in Collection
- In lambda data is stored in functions and variables
- You can think of it as short hand to in writing a method.
- Get the be
```
() -> {}
// () is the argument list
// -> is the lambda expression sytax
// {} is the method body
```
- Lambda Expression method are
```
// OOP
access modifier✅
return type✅
method name✅
curly braces✅
public void m1() {
 System.out.println("Hi");
}

// Lambda expression
access modifier❎
return type❎
method name❎
curly braces❎
MyFunctionalInterface myFunctionalInterface = () -> System.out.println("Hi");
```
- As you can see we almost removed all the unecessary boilerpalte code ending up in concise way of writing a method.
##### Note:
 - If there only 1 line you can remove the curly braces also. but theres 2 or more lines you need to include curly braces.
```
// One line
MyFunctionalInterface myFuntionalInterface = () -> System.out.println();

// Two or more lines
MyFunctionalInterface myFuntionalInterface = () -> {
  // Other code
}
```
 - If argument list is only 1 you can remove also the open/close parenthesis. but there are 2 or more you need to add open/close parenthesis.
```
// One argument
MyFunctionalInterface myFuntionalInterface = arg1 -> System.out.println();

// Two or more argument
MyFunctionalInterface myFuntionalInterface = (args1, args2) -> System.out.println();
```
 - If your lambda has return type and you have only 1 linr of code you dont need to write the return keyword. but if you have a return type and have 2 or more lines ypu need to add return keyword.
```
// One line
MyFunctionalInterface myFuntionalInterface = () -> "Hello World";

// Two or more lines
MyFunctionalInterface myFuntionalInterface = () -> {
  // Other code
  return "Hello World";
}

```

## Pre-defined Functional Interfaces
 - Predicate<T>
   - boolean test(T t)
   #### Predicate chaining
    - Predicate<T> and(Predicate<T> predicate)
    - Predicate<T> or(Predicate<T> predicate)
    - Predicate<T> negate()
 - BiPredicate<T, U>
   - boolean test(T t, U u)
 - Consumer<T>
   - void accept(T t)
   #### Consumer chaining
     - Consumer<T> andThen(Consumer<T> consumer)
 - BiConsumer<T, U>
   - void accept(T t, U u)
 - Function<T, R>
   - R apply(T t)
   #### Function chaining
     - Function<T, R> andThen(Function<T, R> function)
     - Function<T, R> compose(Function<T, R> function)
 - BiFunction<T, U, R>
   - R apply(T t, U u)
 - Supplier<R> 
   - R get()

# Method Reference
# Java 8 Features
- StringJoiner
- Lambda Expression
- @FunctionalInterfaces annotation
- Date Time API
- Stream API
- Optional class
- Static and default methods in interface

# Definition of Terms
- Instatiate = Create
- Implicit = Automatic
- Explicit = Manual
- Sub class, Derived class and Child class are all the same.
- Super class, Base class and Parent class are all the same.
- Method, Function, and Behavior are all the same.
- Field, Property, Variable are all the same.
