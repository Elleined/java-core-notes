# java-core-notes
Java Core Notes

## When you make things faster it will make you slower

## Understand the concept, rather than memorizing the code

Explicit = Manual  
Implicit = Automatic

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
sayHi()✅
eat()✅
```
- **Field** should be noun and use camel casing.
```
name✅
age✅
```
- **Constant Variable** should be in snake case and all caps.
```
PI✅
DEFAULT_VALUE✅
```
##### Note: by writing code base on naming conventions it will make your code readable, able to follow enterprise quality code and when you reading code you can identify amd differentiate right away what is function, variable, and class. 


# Access modifiers
- public: can be used anywhere in the program
- protected: can only be used by child class and not avaiable globally.
- private: only available inside the specific class it was declared on
- package-private: the default access modifier that only available in the specific package it was declared on.
##### Note: In inheritance access modifier cannot be more restricted than the declared one. for example

# Non-access modifiers
- final: use to declare a constant variable, prevent method to be overwritten and also prevent other class to be able extend in class.
- static: is used to the variable and method, class that are not really binded in encapsulating class.
#### Note: static methods and variables should be access via the class itself instead of object instance.
```
Foo.bar()✅
foo.bar()❎
```

# Java common words
- Sub class, Derived class and Child class are all the same.
- Super class, Base class and Parent class are all the same.
- Method, Function, and Behavior are all the same.
- Field and Property are the same.

# Difference of == operator and equals() method
- Double equals only check if two objects memory location are the same.
- equals() method check not the memory locstion but the content of the object.

# Difference of this and super keyword
- this: is used to reference the methods and fields of current object.
- super: used to reference the methods and fields of super class.

# What is class
- Class acts like a blueprint to create an object that has properties = fields and behavior = methods.

# OOP (Object Oriented Programming)
- Meaning is organize the structure of the code thats mimics real world objects via software objects that has their own behavior and properties.
