
# Generics in Kotlin

Generics allow you to write flexible, reusable, and type-safe code in Kotlin. Instead of writing separate logic for each data type, you can write a single logic that works for any type.



## What Are Generics?

Generics let you define a class, function, or interface with a placeholder type that gets specified when you use it.

Example:

```kotlin
class Box<T>(val value: T)
```

Here, `T` is a type parameter. You can use `Box<Int>`, `Box<String>`, and so on.

---

## Examples of Generics

### 1. Generic Class

Wrap any type of value inside a class.

```kotlin
class Box<T>(val value: T) {
    fun get(): T = value
}

// Usage
val intBox = Box(10)
val stringBox = Box("Hello")

println(intBox.get())     // Output: 10
println(stringBox.get())  // Output: Hello
```



### 2. Generic Function

Function that works with any type of list.

```kotlin
fun <T> swap(list: MutableList<T>, index1: Int, index2: Int) {
    val temp = list[index1]
    list[index1] = list[index2]
    list[index2] = temp
}

// Usage
val numbers = mutableListOf(1, 2, 3)
swap(numbers, 0, 2)

println(numbers) // Output: [3, 2, 1]
```



### 3. Generic Interface

Abstract data handling for different models using a common interface.

```kotlin
interface Repository<T> {
    fun save(item: T)
    fun getAll(): List<T>
}

class UserRepository : Repository<User> {
    private val users = mutableListOf<User>()

    override fun save(item: User) {
        users.add(item)
    }

    override fun getAll(): List<User> = users
}

data class User(val id: Int, val name: String)
```



### 4. Generic Constraints

Use `:` to restrict a generic type to a certain type or interface.

```kotlin
fun <T : Number> sum(a: T, b: T): Double {
    return a.toDouble() + b.toDouble()
}

// Usage
println(sum(10, 20))       // 30.0
println(sum(5.5, 4.5))     // 10.0
```

You can also use interfaces like `Comparable`:

```kotlin
fun <T : Comparable<T>> maxOf(a: T, b: T): T {
    return if (a > b) a else b
}
```



### 5. Variance (`in` and `out`)

Variance helps define whether a generic type can produce or consume a value.

#### Covariant (out): Only produces values of type `T`

```kotlin
class Producer<out T>(val item: T) {
    fun produce(): T = item
}
```

#### Contravariant (in): Only consumes values of type `T`

```kotlin
class Consumer<in T> {
    fun consume(item: T) {
        println("Consumed: $item")
    }
}
```



### 6. Generic in Real Projects

#### Example: Generic ViewModel with Repository

```kotlin
class BaseViewModel<T>(private val repository: Repository<T>) : ViewModel() {
    fun loadAll(): LiveData<List<T>> {
        return MutableLiveData(repository.getAll())
    }
}
```



### 7. Generics in Kotlin Collections

Kotlin's built-in collections are generic by default.

```kotlin
val stringList: List<String> = listOf("A", "B", "C")
val intMap: Map<Int, String> = mapOf(1 to "One")
```



## Summary Table

| Feature                | Example                   | Description                       |
| ---------------------- | ------------------------- | --------------------------------- |
| Generic Class          | `class Box<T>`            | Store any type of value           |
| Generic Function       | `fun <T> swap(...)`       | Works with different types        |
| Generic Interface      | `interface Repository<T>` | Reusable data logic               |
| Bounded Generics       | `<T : Number>`            | Restrict type to a specific class |
| Variance (`in`, `out`) | `out T`, `in T`           | Control how generics are used     |


