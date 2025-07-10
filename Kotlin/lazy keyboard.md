
#  Kotlin `lazy` Keyword Explained

This repository demonstrates how to use the `lazy` keyword in Kotlin with a simple example. The code is designed to run on [Kotlin Playground](https://play.kotlinlang.org/) and showcases lazy initialization.



##  What is `lazy` in Kotlin?

`lazy` is a built-in Kotlin feature that allows **lazy initialization** of values. That means the value is **computed only once** and **only when it's first accessed**.



##  Why Use `lazy`?

-  Avoid unnecessary computation
-  Efficient resource usage
-  Clean syntax for deferred initialization
-  Thread-safe by default (using `SYNCHRONIZED` mode)



##  Example

```kotlin
fun main() {
    println("Start")

    val myLazyValue: String by lazy {
        println("Computing lazy value...")
        "Lazy Initialized!"
    }

    println("Before accessing lazy value")
    println(myLazyValue) // First access: triggers the block
    println(myLazyValue) // Second access: returns cached value
}
````

###  Output:

```
Start
Before accessing lazy value
Computing lazy value...
Lazy Initialized!
Lazy Initialized!
```



##  Thread Safety Modes

Kotlin provides 3 modes for lazy:

* `SYNCHRONIZED` *(default)* – safe for multi-threaded access
* `PUBLICATION` – allows multiple threads to initialize, but only one result is used
* `NONE` – no thread safety; fastest but for single-threaded use

```kotlin
val lazyValue: String by lazy(LazyThreadSafetyMode.NONE) {
    "Fast but not thread-safe"
}
```



##  Use Cases

* Delay loading of large data
* Lazy config initialization
* Expensive computations
* Dependency injection scenarios

###  Author

**Shreyash Pattewar**
*Android Developer*


