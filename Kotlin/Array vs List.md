# Array vs List Performance in Kotlin

This document demonstrates the difference in performance between **Array** and **ArrayList** in Kotlin when iterating over a large collection of integers.

---

## Benchmark Code

```kotlin
import kotlin.system.measureTimeMillis

fun main() {
    val size = 10_000_000
    val list = ArrayList<Int>(size)
    val arr = Array(size) { it }

    for (i in 0 until size) {
        list.add(i)
    }
    testArray(arr)
    testList(list)
}

fun testArray(arr: Array<Int>) {
    val arrayTime = measureTimeMillis {
        var sum = 0L
        arr.forEach { sum += it }
        println("Array sum: $sum")
    }
    println("Array elapsed: ${arrayTime / 1000.0} sec")
}

fun testList(list: ArrayList<Int>) {
    val listTime = measureTimeMillis {
        var sum = 0L
        list.forEach { sum += it }
        println("List sum: $sum")
    }
    println("List elapsed: ${listTime / 1000.0} sec")
}
````

---

## Sample Output

```
Array sum: 49999995000000
Array elapsed: 0.007 sec
List sum: 49999995000000
List elapsed: 0.012 sec
```

---

## Key Differences Between Array and List

| Feature         | Array                                         | ArrayList (List)                                                   |
| --------------- | --------------------------------------------- | ------------------------------------------------------------------ |
| **Size**        | Fixed at creation                             | Dynamic, can grow or shrink                                        |
| **Memory**      | Stores elements in contiguous memory          | Internally backed by an array; may reallocate when resizing        |
| **Access Time** | O(1) for index access                         | O(1) for index access, slightly slower due to abstraction          |
| **Performance** | Faster for iteration and primitive operations | Slightly slower due to additional abstraction and dynamic resizing |
| **Use Case**    | Known size collections, performance critical  | Flexible collections where size may change                         |

---

## Conclusion

* **Arrays** are slightly faster than **ArrayLists** in Kotlin for large collections, especially when iterating or performing simple operations.
* **ArrayLists** are more flexible but come with minor performance overhead.
* For **primitive-heavy operations**, prefer `IntArray` or `Array<Int>` to avoid boxing/unboxing overhead.


###  Author
**Shreyash Pattewar**
*Android Developer*
