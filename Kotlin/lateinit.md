 

##  `lateinit` Keyword in Kotlin

The `lateinit` keyword is used for **late initialization** of non-null `var` properties — primarily when you don’t want to initialize a variable during object construction, but **you promise** to initialize it before use.

---

###  Rules of `lateinit`

* Can only be used with **non-nullable `var`** properties.
* Cannot be used with **primitive types** like `Int`, `Double`, `Boolean`, `Char`, etc.
* Works **only with class-level properties**, not local variables inside functions.
* Use `::propertyName.isInitialized` to check if a `lateinit` property is initialized.

---

###  Code Example

```kotlin
fun main() {
    val person = Person()

    person.printName()     // Not initialized

    person.name = "Shreyash"

    person.printName()     // Initialized
}

class Person {
    lateinit var name: String

    // lateinit var number: Char ❌ Not allowed for primitive types

    fun printName() {
        if (::name.isInitialized) {
            println("Name is initialized: $name")
        } else {
            println("Name is NOT initialized")
        }
    }
}
```

---

###  Sample Output

```
Name is NOT initialized
Name is initialized: Shreyash
```

---

### ⚠ Common Mistakes

| Mistake                     | Why It's Wrong                                     |
| --------------------------- | -------------------------------------------------- |
| `lateinit var number: Int`  |  Not allowed for primitive types                  |
| `lateinit val name: String` |  Must be a `var`, not `val`                       |
| Using inside `fun`          |  `lateinit` cannot be used on **local variables** |

---

###  Use Cases

* Dependency injection (`lateinit var viewModel: MyViewModel`)
* Views in Android (`lateinit var textView: TextView`)
* Unit testing mock setup (`lateinit var mockService: ApiService`)

 ###  Author

**Shreyash Pattewar**
*Android Developer*
