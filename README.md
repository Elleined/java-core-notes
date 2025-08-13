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

extends
- T and all of its childclasses, subtypes
- (Producers Extends) means reading a value and literally producing a value
- Safe for reading, unsafe for writing
- So mental model is extends means: "I'm reading Ts"
- Upperbound

super
- T and all of its superclasses, supertypes
- (Consumer Super) means writing a value and literally consuming a value
- Safe for writing, unsafe for reading
- So mental model is super means: "I'm writing Ts"
- Lowerbound

Object
  └── Number
        ├── Integer
        └── Double

List<? extends Number>
   Could be: List<Number>, List<Integer>, List<Double>

List<? super Integer>
   Could be: List<Integer>, List<Number>, List<Object>


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

# Exception handling

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

# What is Aggregation
- Using other class as class member of another class for example.
```
public class Person {
  private Car car;
}

private class Car {
  private Engine engine;
}

private class Engine { }
```

##### When to use aggregation
- Use aggregation if you need a dependency from other class or you that class as class member. and has a relation of that can be read as 'has a' for example:
   - Person has a Car
   - Car has a Engine
   
##### Difference between aggregation and inheritance
- Nowadays aggregation are preferred instead of inheritance because it much more easy and quick to implement. But I prefer to use inheritance because when you don't use inheritance you will end up writing many code because your classes are not related and you can't reuse code because aggregation introduces coupling.

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
```
// Without lambda expression
public interface Adder<T, U> {
  void add(T num1, U num2);
}

public class IntegerAdder implements Adder<Integer, Integer> {
 @Override
public void add(Integer num1, Integer n2) {
  System.out.println(num1 + num2);
}

// With lambda expression
Adder<Integer, Integer> integerAdder = (num1, num2) -> System.out.println(num1 + num2);

() -> {}
// () is the argument list
// -> is the lambda expression sytax
// {} is the method body
```
- Lambda expression compare to OOP
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

##### Question: How does JVM knows what is return type, access modifier, , parameter list, and method name if we removed it?
##### Answer: JVM will reference based on the method signature you defined in you functional interface thats why it can determine which method to call, what is return type, what is access modifier, parameter list, and method name.

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
   ```
   Predicate<T> and(Predicate<T> predicate)
   Predicate<T> or(Predicate<T> predicate)
   Predicate<T> negate()
   ```
 - BiPredicate<T, U>
   - boolean test(T t, U u)
 - Consumer<T>
   - void accept(T t)
   #### Consumer chaining
   ```
   Consumer<T> andThen(Consumer<T> consumer)
   ```
 - BiConsumer<T, U>
   - void accept(T t, U u)
 - Function<T, R>
   - R apply(T t)
   #### Function chaining
   ```
   Function<T, R> andThen(Function<T, R> function)
   Function<T, R> compose(Function<T, R> function)
   ```
 - BiFunction<T, U, R>
   - R apply(T t, U u)
 - Supplier<R> 
   - R get()

#### Conclusion for lambda expression
-  The traditional way of OOP is to implement a FunctionalInterface and create a new class that implements it. And when you need another behavior you will create new class and implement it again which leads to class explosion, more boilerplate code, and ugly code. That's why we need lambda expression to avoid that and also achieve functional programming.

# Method Reference
- Is used replace lambda expression with existing method to maintain code readability and security.
- :: symbol is used to reference to method.
 
#### 4 types of method reference
- **static reference**
```
ClassName::staticMethod
```
- **instance method of other object**
```
otherObject::instanceMethod
```
- **instance method of specific object your working on**
```
specificObject::instanceMethod
```
- **constructor reference**
```
ClassName::new
```

##### When writing method reference () of refering method is not required just the name of the method reference.

##### You can think method reference as lambda in form of just normal method asa you notice lambda is just short hand syntax of method so if you want your lambda to have name you can use method reference.

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

# IO
## 2 Types of Streams in Java
### Bytes
- InputStream == Read
- OutputStream == Write
###### Any thing that ends with Stream its used for bytes
![download_file](https://github.com/Elleined/java-core-notes/assets/111877930/6292059d-403a-4570-b9c7-f6ed059ff226)

### Character
- Writer = Writing
- Reader = Reading
###### Anything that ends with reader or writer its used for characters
![download_file (1)](https://github.com/Elleined/java-core-notes/assets/111877930/46b1f7f4-bcba-4b4b-9826-175f3c611319)


File Used for
Represent files or directort
- existence of files and directory
- read, write, delete, and manage files

# Path, Paths, and Files comes from java.nio that stands for new io the replacement for java.io package.


# Path
Represents path to a file or directory 
- automatic separators based on os
- Works well with Files
- Part ng java.nio package

# Paths
A utility class to create a Path object

# Files
A utility class to perform I/O operations in Path object

- provides Single or batch procesising of move, copy, delete, read and write files
- check for existence
- part of java.nio package stands for new io 


# Conclusion
Basically File object is used for legacy codes below java 7 but when java 7 comes it comes with new io package which is named java.nio meaning java new io package meant to replace the old java.io and comes with Path, Paths, and Files which is more flexible and maintainable. Where Paths and Files are utility classes to work with Path objrct easily so that when you are  dealing with io operstion used Path, Paths, and Files.

# Variance
## Covariance
- Is the subtypes and more specific types
- Provide safety in returns and not safe in parameters
- Subtype returns
- Subtype returns the subtypes or the same as the supertype returns
### Be conservative in what you do. Only means that you return a more specific type becauae you are strict of what you do.

## Contravariance
###### Not supported in java it will just overload not override. But can be done using generics

- Is the supertypes and more generalized types
- Supertype parameters
- Provide safety in parameters and not safe in returns
- Subtype accepts supertypes as parameters
### Be liberal of what you accept from others. Only means that you accept supertypes as parameters because you are not strict of what they supply to you.

# Threads
# Virtual Thread
## When to use virtual thread and native thread
- Only use virtual thread for IO operation and Native thread for computationally expensive operation, You will say why? It's because virtual threads are using native threads behind the scene and native thread are executing in cpu an IO operation doesnt use cpu continously its just waiting for the cpu to finish processing an IO operstion unlike computationally expensive operation its using cpu continously executing operation line by line sequencially meaning that native thread when executing a computationally heavy operation are only mounted once unlike IO operation since its just waiting for the cpu to finish we can use virtual thread to mount and unmount operation like IO operation.

## How does virtual thread works behind the secene
- Virtual thread are using native thread behind the scene by the way native thread are on operating system level resource and virtual thread is just a piece of memory(an object in jvm). Going back before java 21 we can say that one task one native thread right? So if we a blocking operation we create more native threads to handle the system load which is very not recommended because you are limited in resources and scaling is just nightmare expending millions investing in machines. But java 21 introduced virtual threads where now one task is one virtual thread take note "one task per one virtual thread" not before one task one native thread, what virtual thread does its get mounted and unmounted in native thread so the native thread now a queue executor of virtual thread where the virtual thread will get mounted in native thread and if that virtual thread has an IO operstion that need to be executed in cpu it will not wait for that operstion to finished it will get unmounted for the meantime letting other virtual thread to be executed in cpu and once the cpu finished the execution of the task the virtual thread will get the result and now execute again from the program.


###### Note
- Virtual threads are like cotton buds that are only meant to be used and throw because they are just java objects remember u like native thread that are operating in OS level which resource intensive.

# Blocking operation
## Analogy
- Imagine you want a coffee and the coffee machine is non operational and you did is just stare at the coffee machine praying it will be fixed someday and you will get stuck there forever in that coffee machine waiting to be fixed. That's what you call a blocking operation where you will just wait for the operation to be finished before doing other things.

- Thread is used to execute a java code when you run a java in your main class that is the main thread and you can have many threads in your application. Remember multithreading concept. So now what is Threadblocking because java execute lines of code sequentially meaning it will wait for the line of code to be finish before getting into next line. so now imagine you have expensive operation in that line of code it will wait for that code to finish before executing the rest of the code and finally the thread will be release and ready for the next task or ready to be used again.

# Non blocking operation
## Analogy
-  Imagine the same scenario you want a coffee and the coffee machine is non operational you will do is leave the coffee machine for the meantime and do other things like checking email, attending meetings, etc... and when the coffee machine gets fixed you will now go back to the coffee machine and get your favorite coffee. That's what you call a non blocking operation where you will do other things while waiting for the task to get finished.
