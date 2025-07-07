 
## `const val` vs `val` in Kotlin

In Kotlin, `const val` is used for **compile-time constants**, while `val` can hold **runtime-evaluated values**.

---

### 💡 Key Differences

| `const val`                                        | `val`                       |
| -------------------------------------------------- | --------------------------- |
| Must be **top-level** or in an `object`            | Can be declared anywhere    |
| Known at **compile time**                          | Evaluated at **runtime**    |
| Can only hold **primitive types and Strings**      | Can hold any type           |
| Can’t use things like `System.currentTimeMillis()` | Can use runtime expressions |

---

###  Working Example

```kotlin
fun main() {
    val person = Person("manage/home")
    person.printName()
}

// ✅ Compile-time constant
const val URL = "https://api.example.com/"

// ❌ Not allowed – not a compile-time constant
// const val time = System.currentTimeMillis()

class Person() {
    var home = ""

    constructor(home: String) : this() {
        this.home = home
    }

    fun printName() {
        print("${URL}${home} ")
    }
}
```

---

###  Output

```
https://api.example.com/manage/home
```

---

###  Common Error

```kotlin
const val time = System.currentTimeMillis()
//  Error: const val requires a compile-time constant
```

Use this instead:

```kotlin
val time = System.currentTimeMillis() //  Allowed
```

---

###  Summary

* Use `const val` for constants like URLs, keys, and static strings.
* Use `val` for values you get during runtime (like timestamps, UUIDs, etc.).
* `const` improves performance slightly as it's embedded directly into bytecode.


