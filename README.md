# CodeSnippet

 

This Kotlin class demonstrates how **primary** and **secondary constructors** work alongside `init` blocks. It prints debug output to show the **execution order** when different constructors are used.

 

## ⚙️ How Initialization Works

- The `init` blocks are executed **immediately after the primary constructor**.
- **Secondary constructors** must delegate to the primary one, meaning the `init` blocks are executed **before** the secondary constructor’s logic.
- The debug print statements show how values like `name`, `email`, and `phone` are initialized at different stages.

 

## 🔍 Code Snippet

```kotlin
class Person(var name: String) {

    var email: String = ""
    var phone: String = ""

    init {
        println("1st init block \n{ Name: $name Email: $email }\n")
    }

    constructor(name: String, email: String) : this(name) {
        this.email = email
        println("1st Constructor block \n{ Name: $name Email: $email }\n")
    }

    constructor(name: String, email: String, phone: String) : this(name) {
        this.email = email
        this.phone = phone
        println("1st Constructor block \n{ Name: $name Email: $email Phone: $phone }\n")
    }

    init {
        println("2nd init block \n{ Name: $name Phone: $phone }\n")
    }
}
````

---

## 🧪 Example Usage

```kotlin
fun main() {
    val person1 = Person("Shreyash")
    val person2 = Person("Shreyash", "shreyashp47@gmail.com")
    val person3 = Person("Shreyash", "shreyashp47@gmail.com", "8806308XXX")
}
```

---

## 📤 Sample Output

```
1st init block 
{ Name: Shreyash Email:  }

2nd init block 
{ Name: Shreyash Phone:  }

1st init block 
{ Name: Shreyash Email:  }

2nd init block 
{ Name: Shreyash Phone:  }

1st Constructor block 
{ Name: Shreyash Email: shreyashp47@gmail.com }

1st init block 
{ Name: Shreyash Email:  }

2nd init block 
{ Name: Shreyash Phone:  }

1st Constructor block 
{ Name: Shreyash Email: shreyashp47@gmail.com Phone: 8806308XXX }
```

---

## 💡 Key Concepts Demonstrated

* Constructor chaining in Kotlin
* `init` block execution order
* Overloaded constructors
* Class property initialization and default values

---

## 🙋 Author

**Shreyash Pattewar**
*Android Developer*

 
 
