[//]: # (title: Basic syntax)

This is a collection of basic syntax for Kotlin with their equivalent in C++.

YThe Kotlin essentials can be learned over at the [Kotlin Basics track](https://hyperskill.org/tracks/18)
on the JetBrains Academy.

## Semi Colons

Kotlin has largely dispensed with the need for semi-colons to terminate statements. It is encouraged in Kotlin not to use semi-colons. There may be situtations where a semi-colon is required, however, the compiler will 
inform the user where a statement is ambiguous, and will tell you where to insert a semi colon.

```kotlin

fun sum(a: Int, b: Int) : Int
{
   return a + b //No need to terminate a statement with a semi-colon
}
```

In C++ semi colons are ubiquitous and used to delimit statements, declarations, and class and structure definitions.
For example:

``` cpp
int myVariable = 42;   //Semi-colon delimiting a variable
int sum(int a, int b); //Semi-colon delimiting a function prototype

class myClass
{
  int member;    //Semi-colons delimiting members and methods
  void method();
};               //Semi-colon delimiting a class declaration
  
int sum(int a, int b)
{ 
  return a + b;        //Semi-colon deliminting a statement
}
```