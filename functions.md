# Functions

**Where to begin?** Start with [Kotlin docs - Functions﻿](https://kotlinlang.org/docs/functions.html)   

--------

## C++ VS Kotlin // Passing parameters

### Parameters are immutable
- [Ref](https://blog.jetbrains.com/kotlin/2013/02/kotlin-m5-1/)  
- [Kt Example](https://godbolt.org/z/8PvacfzWe)
- [C++ Example](https://godbolt.org/z/8qYq4Ysed)

Passing a primitive to a function, and mutating it.  

Koltin:  
```
fun test(value: Int) {
    value = 4     // This does not compile (error: val cannot be reassignedkotlinc 1.6.10 #1)
    print("value in test: $value")
}

fun main() {
    val value = 5
    print("value in main: $value")
    test(value)
    print("value in main after test(): $value")
}
```

Output:
`error: val cannot be reassignedkotlinc 1.6.10 #1`

C++:
```
#include <fmt/core.h>

void test(int value) {
    value = 4;
    fmt::print("value in test: {}\n", value);
}

int main() {
    auto value = 5;
    fmt::print("value in main: {}\n", value);
    test(value);
    fmt::print("value in main after test(): {}\n", value);
}
```

Output:
```
value in main: 5
value in test: 4
value in main after test(): 5
```

### Passing class with mutable member

- [Kt Example](https://godbolt.org/z/hvPMcKhcs)
- [C++ Example](https://godbolt.org/z/xbjdr5q74)

In this example, we have a simple class which has a mutable member,  
when passing an instance of `MyClass` to a function,  
when function is called with `MyClass` it will modify the member.
Observe the behavour in output between Kt and C++

```
data class MyClass(var value: Int)

fun test(myClass: MyClass) {
    myClass.value = 4
    println("value in test: $myClass")
}

fun main() {
    val myClass = MyClass(5)
    println("value in main: $myClass")
    test(myClass)
    println("value in main after test(): $myClass")
}
```

Output:
```
value in main: MyClass(value=5)
value in test: MyClass(value=4)
value in main after test(): MyClass(value=4)
```


```
#include <fmt/core.h>

struct MyClass {
    int value;
};

void test(MyClass myClass) {
    myClass.value = 4;
    fmt::print("value in test: {}\n", myClass.value);
}

int main() {
    auto myClass = MyClass{5};
    fmt::print("value in main: {}\n", myClass.value);
    test(myClass);
    fmt::print("value in main after test(): {}\n", myClass.value);
}
```

Output:
```
value in main: 5
value in test: 4
value in main after test(): 5
```

Let's modify the C++ example, to pass by ref:
- [C++ Example](https://godbolt.org/z/5TzP11Eor)

```c++
void test(MyClass& myClass) {
```

The, c++ output will change to this:
```
value in main: 5
value in test: 4
value in main after test(): 4
```
