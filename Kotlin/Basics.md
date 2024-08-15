# Kotlin Basics

## Print functions

```kotlin
val name = "World"
print("Hello, World!")
println("Hello, World!")

println("Hello, $name!)
println("Hello, " + name + "!")
```

- `print` functions prints the output on the same line without moving the cursor to the nsext line
- `println` does the opposite

> A very important thing to note here is that the kotlin does not need semicolons to end a statement

## Variables and Data Types

```kotlin
val name = "Anirudh"
var name1 = "Anirudh"
```

- `val` keyword specifies that the variable cannot reference to any object other than the given one
- `var` keyword tells that the variable's value can be changed / updated

> Almost all operators used in other languages, can be used here

```kotlin
val name: String = "Anirudh"
val name1 = "Anirudh"
```

- In the above example, both assignments are correct as kotlin supports something called `type inferenece` which automatically takes assumes the data type of a variable

## Conditionals

```kotlin
val myage = 19
if (myage > 18) {
    println("Adult")
} else {
    println("Under Age")
}
```

- Conditional statements are similar to those in other languages

## Collections

```kotlin
val arr = listof(1, 2, 3, 4, 5)
println(arr);
```

- Here `listof` is a function which creates a list of integers.
- Note that we can directly print the whole list using the print statements
- `val arr  = listof(1, 2, 3, 4, 5)` is similar to `val arr  = listof<Int>(1, 2, 3, 4, 5)`
- A list can store multiple types of values together

```kotlin
val arr = listof<Any>("Hello", 'A', 1, 6.5, true)
```

- Lists are, by default, immutable. They can be made mutable using the function `mutableListof()`

## Loops

```kotlin
for(i in 1 .. 4) {
    println(i)
}
```

```kotlin
var index = 0
while (index <= 9) {
    println(i)
    index++
}
```

## Functions

- Functions are created using the keyword `fun`

```kotlin
fun add(a: Int, b: Int) : Int {
    return (a + b)
}
```

- Here `: Int` specifies the return type
- The above code can be rewritten as

```kotlin
fun add(a: Int, b: Int) : Int = (a + b)
```

- This offeres the same functionality as the above code
- Any class or file can access a function in a different class or file as they are defaulted to `public` visibility. We can change this by using the keyword `private`.

## Null Safety

- A variable can have no value (null)
- It will be dangerous to operate on or call a function on a null variable

```kotlin
val data : String? = null
```

- `?` means that if there is some data given to the variable, it will store it. Otherwise, it is null
- There are many methods to check if a variable is null

```kotlin
val data : String? = null
if (data != null) {
    println(data.lowercase())
} 

println(data?.uppercase)
```

- An if statement or the variable with `?` can be used to check the data beforehand