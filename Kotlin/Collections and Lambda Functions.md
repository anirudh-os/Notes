# Collections and Lambda Functions

## Set

```kotlin
val s = setof(1, 2, 3, 4, 5)
```

- It doesn't store duplicate elements
- They do not support indexing

```kotlin
fun main() {
    val user1 = User("Anirudh")
    val user2 = User("Anirudh")
    val user3 = User("Alakh")
    val user4 = User("Andrew")

    val s = setOf(user2, user1, user3, user4)
    println(s)

    s.forEach {println(it.name)}
}
class User(val name: String)
```

```bash
[User@37a71e93, User@7e6cbb7a, User@7c3df479, User@7106e68e]
Anirudh
Anirudh
Alakh
Andrew
```

- Although a set doesn't contain duplicate elements, objects are considered to be unique (compares the address) as the class isn't declared to be a `data class`
    - A *_Data Class_* is a special type of class used to store data elements. The compiler provides functions like `hashcode()` or `equals()`
- Therefore if we declare the class to be a data class, then

```bash
[User(name=Anirudh), User(name=Alakh), User(name=Andrew)]
Anirudh
Alakh
Andrew
```

- Here the properties of each object are also compared and that's why the duplicate data isn't printed

## Maps

```kotlin
fun main() {
    val map_collection = mapOf<Int, String>(1 to "home", 2 to "college", 3 to "shop")

    map_collection.forEach { t, u ->
        println("$t to $u")
    }
}
```

- Maps are key - value pairs
- They are not indexed
- Duplicate values are allowed but duplicate keys are not allowed
- They can be mutable

```kotlin
fun main() {
    val mapcollection = mutableMapOf<Any, Any>(1 to "home", 2 to "college", 3 to "shop")

    println("Before Changing: ")
    mapcollection.forEach { (t, u) ->
        println("$t to $u")
    }

    mapcollection[4] = 6

    println("After Changing: ")
    mapcollection.forEach { (t, u) ->
        println("$t to $u")
    }
}
```

```bash
Before Changing: 
1 to home
2 to college
3 to shop
After Changing: 
1 to home
2 to college
3 to shop
4 to 6
```

## Lambda Functions

```kotlin
fun main() {
    val  lambdaadd = {a: Int, b: Int -> println("a + b = ${a + b}")}

    lambdaadd(72, 81) // a + b = 153
}
```

- Custom one-line functions which can be called by a variable

```kotlin
fun main() {
    val  lambdaadd = {a: Int, b: Int -> println("a + b = ${a + b}")}

    doer(10, 15, lambdaadd) // a + b = 25
}

fun doer(a: Int, b:Int, action: (Int, Int) -> Unit) {
    action(a, b)
}
```

- A lambda function can be passed as an argument to another function
- `action`[^1] and `Unit`[^2] have specific meanings in kotlin

[^1]: `action` is a parameter of type (Int, Int) -> Unit. The name action is not mandatory; it's simply a name chosen for clarity and readability.
[^2]: `Unit` is a type in Kotlin that represents a function's return type when it does not return any meaningful value. It is similar to void in Java or C/C++. However, unlike void, Unit is an actual type in Kotlin, and it has a singleton object called Unit which is returned by functions that don’t return any other value.

```kotlin
fun main() {

    doer(10, 15) {a: Int, b: Int -> println("a + b = ${a + b}")}
}

fun doer(a: Int, b:Int, action: (Int, Int) -> Unit) {
    action(a, b)
}
```

- The lambda function to be passed can be defined outside the paranthesis

## Common Collection Functions

1. Transformation Functions

- map: Transforms each element in a collection using a provided function and returns a new collection with the transformed elements.

```kotlin
val numbers = listOf(1, 2, 3)
val squares = numbers.map { it * it } // [1, 4, 9]
```

```kotlin
fun main() {
    val s = setOf(1, 2, 3, 4, 5)
    println(s.map { if (it <= 3) it + 3 else it - 3 }) // [4, 5, 0, 1, 2]
}
```

```kotlin
fun main() {
    val s = setOf(1, 2, 3, 4, 5)
    println(s.map {
        when {
            it < 3 -> it + 3
            it > 3 -> it - 3
            else -> 3
        }
    }) // [4, 5, 3, 1, 2]
}
```

- flatten - Combines all the elements of a collection into a single collection, if each one of those elements is a collection itself

```kotlin
fun main() {
    val numsets = listOf(setOf(1, 2, 3), setOf(4, 5, 6), setOf(7, 8, 9))

    val num = numsets.flatten()

    println(numsets)
    println(num)
    /* [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
       [1, 2, 3, 4, 5, 6, 7, 8, 9] */
}
```

- flatMap: Transforms each element into a collection and then flattens the results into a single collection. There can be some transformations applied on each of those elements

```kotlin
val lists = listOf(listOf(1, 2), listOf(3, 4))
val flattened = lists.flatMap { it } // [1, 2, 3, 4]
```

- filter: Returns a collection containing only elements that match the given predicate.

```kotlin
val numbers = listOf(1, 2, 3, 4)
val evenNumbers = numbers.filter { it % 2 == 0 } // [2, 4]
```

- filterIndexed(): Filters the given collection and returns the same type of collection by checking if the indices and values which match the given predicate

```kotlin
fun main() {
    val numbers = listOf("One", "Two", "three", "Four")
    val filteredByIndex = numbers.filterIndexed { index, value -> (index > 0) && (value.first().isUpperCase()) }

    println(filteredByIndex) // [Two, Four]
}
```

- filterNot: Returns a collection containing only elements that do not match the given predicate.

```kotlin
val numbers = listOf(1, 2, 3, 4)
val oddNumbers = numbers.filterNot { it % 2 == 0 } // [1, 3]
```

- filterIsInstance(): It is used to filter elements based on their type

```kotlin
fun main() {
    val mixed = listOf("One", "Two", "three", "Four", 1, 2, 3, 4, 'A', 'B', 'C', 'D', true, false)

    mixed.filterIsInstance<Char>().forEach {
        print("$it ")
    } // A B C D
}
```

- partition(): It seperates the collection into two collections, one containing the values satisfying the predicate and the other one having the rest

```kotlin
fun main() {
    val mixed = listOf("One", "Two", "three", "Four", 1, 2, 3, 4, 'A', 'B', 'C', 'D', true, false)

    val (match, rest) = mixed.partition { it is Int}

    println(match)
    println(rest)
    /* [1, 2, 3, 4]
       [One, Two, three, Four, A, B, C, D, true, false] */
}
```

- mapNotNull: Transforms each element and filters out null results.

```kotlin
val strings = listOf("1", "2", "abc")
val numbers = strings.mapNotNull { it.toIntOrNull() } // [1, 2]
```

- distinct: Returns a collection containing only distinct elements.

```kotlin
val numbers = listOf(1, 2, 2, 3)
val distinctNumbers = numbers.distinct() // [1, 2, 3]
```

2. Aggregation Functions

- sum: Returns the sum of all elements in a collection of numbers.

```kotlin
val numbers = listOf(1, 2, 3)
val sum = numbers.sum() // 6
```

- average: Returns the average of all elements in a collection of numbers.

```kotlin
val numbers = listOf(1, 2, 3)
val average = numbers.average() // 2.0
```

- min / max: Returns the minimum/maximum element in a collection.

```kotlin
val numbers = listOf(1, 2, 3)
val min = numbers.minOrNull() // 1
val max = numbers.maxOrNull() // 3
```

- reduce: Applies a binary operation to all elements and returns a single result.

```kotlin
val numbers = listOf(1, 2, 3)
val sum = numbers.reduce { acc, i -> acc + i } // 6
```

- fold: Similar to reduce, but allows specifying an initial value.

```kotlin
val numbers = listOf(1, 2, 3)
val sum = numbers.fold(10) { acc, i -> acc + i } // 16
```

3. Query Functions

- any: Checks if any element matches the given predicate.

```kotlin
val numbers = listOf(1, 2, 3)
val hasEven = numbers.any { it % 2 == 0 } // true
```

- all: Checks if all elements match the given predicate.

```kotlin
val numbers = listOf(1, 2, 3)
val allPositive = numbers.all { it > 0 } // true
```

- none: Checks if no elements match the given predicate.

```kotlin
val numbers = listOf(1, 2, 3)
val noNegative = numbers.none { it < 0 } // true
```

- find: Returns the first element matching the given predicate, or null if none match.

```kotlin
val numbers = listOf(1, 2, 3)
val firstEven = numbers.find { it % 2 == 0 } // 2
```

- count: Counts the number of elements matching the given predicate.

```kotlin
val numbers = listOf(1, 2, 3)
val evenCount = numbers.count { it % 2 == 0 } // 1
```

4. Sorting and Grouping Functions

- sorted: Returns a sorted list of elements.

```kotlin
val numbers = listOf(3, 1, 2)
val sortedNumbers = numbers.sorted() // [1, 2, 3]
```

- sortedBy / sortedDescending: Sorts elements based on a given selector or in descending order.

```kotlin
val numbers = listOf(3, 1, 2)
val sortedByDescending = numbers.sortedDescending() // [3, 2, 1]
```

- groupBy: Groups elements by a key and returns a map where keys are the group keys and values are lists of elements in each group.

```kotlin
val numbers = listOf(1, 2, 3, 4, 5)
val grouped = numbers.groupBy { it % 2 } // {1=[1, 3, 5], 0=[2, 4]}
```

5. Modifying Functions

- add() and addAll()

    - add(element): Adds a single element to a MutableCollection.

    - addAll(elements): Adds all elements from a specified collection to a MutableCollection.
```kotlin
fun main() {
    val numbers = mutableListOf(1, 2, 3)
    
    numbers.add(4) // Adds 4 to the list
    numbers.addAll(listOf(5, 6)) // Adds 5 and 6 to the list
    
    println(numbers) // Output: [1, 2, 3, 4, 5, 6]
}
```

- remove() and removeAll()
    - remove(element): Removes a single occurrence of the specified element from a MutableCollection.
    - removeAll(elements): Removes all occurrences of the specified elements from a MutableCollection.
```kotlin
fun main() {
    val numbers = mutableListOf(1, 2, 3, 4, 5)
    
    numbers.remove(3) // Removes the element 3 from the list
    numbers.removeAll(listOf(4, 5)) // Removes the elements 4 and 5
    
    println(numbers) // Output: [1, 2]
}
```
- clear()
    - clear(): Removes all elements from the MutableCollection.
```kotlin
fun main() {
    val numbers = mutableListOf(1, 2, 3, 4, 5)
    
    numbers.clear() // Removes all elements from the list
    
    println(numbers) // Output: []
}
```
- retainAll()
    - retainAll(elements): Retains only the elements in the MutableCollection that are contained in the specified collection.
```kotlin
fun main() {
    val numbers = mutableListOf(1, 2, 3, 4, 5)
    
    numbers.retainAll(listOf(2, 4)) // Keeps only the elements 2 and 4
    
    println(numbers) // Output: [2, 4]
}
```

- sort() and reverse() (for MutableList)
    - sort(): Sorts the elements of a MutableList in-place.
    - reverse(): Reverses the order of elements in a MutableList.
```kotlin
fun main() {
    val numbers = mutableListOf(5, 3, 1, 4, 2)
    
    numbers.sort() // Sorts the list in ascending order
    println(numbers) // Output: [1, 2, 3, 4, 5]
    
    numbers.reverse() // Reverses the order of elements
    println(numbers) // Output: [5, 4, 3, 2, 1]
}
```

> Note: Except these modifying functions, all other functions on collections return the transformed version of the collection they are operating on.

6. Zipping and Association

- zip(): Makes pairs of elements of two collections at the same index
```kotlin
fun main() {
    val n1 = listOf(1, 2, 2, 4, 5)
    val n2 = listOf(1, 21, 3, 4, 5)

    println(n1.zip(n2)) 
    println(n1 zip n2) 
    /* [(1, 1), (2, 21), (2, 3), (4, 4), (5, 5)]
       [(1, 1), (2, 21), (2, 3), (4, 4), (5, 5)] */
}
```
```kotlin
fun main() {
    val colors = listOf("red", "brown", "grey")
    val animals = listOf("fox", "bear", "wolf")

    println(animals.zip(colors) {animal, color -> "The ${animal.replaceFirstChar {it.uppercase()}} is $color"})
    // [The Fox is red, The Bear is brown, The Wolf is grey]
}
```

- unzip(): Used to seperate pairs

```kotlin
fun main() {
    val pairs = listOf("One" to 1, "Two" to 2, "Three" to 3)

    println(pairs)
    println(pairs.unzip())
    /* [(One, 1), (Two, 2), (Three, 3)]
       ([One, Two, Three], [1, 2, 3]) */
}
```

- associateWith(): Takes a collection as a parameter and creates a map with the elements of the collection as keys and the result of transformation on each of those as their values

```kotlin
fun main() {
    val list = listOf("One", "Two", "Three")

    println(list.associateWith { it.length }) // {One=3, Two=3, Three=5}
}
```

- associateBy(): Creates a map with keys as the result of transformations on the elements of the collection and values as the elements themselves

```kotlin
fun main() {
    val list = listOf("One", "Two", "Three", "Four")

    println(list.associateBy { it.first().uppercase() }) // {O=One, T=Three, F=Four} 
                                                        // One 'T' is omitted because there cannot be duplicate keys
}
```
```kotlin
fun main() {
    val list = listOf("One", "Two", "Three", "Four")

    println(list.associateBy(keySelector = {it.first().uppercase()}, valueTransform = {it.length})) 
    // {O=3, T=5, F=4}
    // Both key and value can be the transformed value of the original elements
}
```

7. String Representation

- joinToString(): It combines all of the string elements of the collection into one string
    - Default seperator is ','

```kotlin
fun main() {
    val numStrings = listOf("one", "two", "three", "four")
    
    println(numStrings.joinToString()) // one, two, three, four
}
```

```kotlin
fun main() {
    val numStrings = listOf("one", "two", "three", "four")

    println(numStrings.joinToString(separator = ", ", prefix = "The numbers are: ", postfix = ".")) // The numbers are: one, two, three, four.
}
```

```kotlin
fun main() {
    val numbers = (1 .. 100).toList()

    println(numbers.joinToString(limit = 15, truncated = "..., ${numbers[numbers.size - 1]}")) // 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, ..., 100
}
```

```kotlin
fun main() {
    val numStrings = listOf("one", "two", "three", "four")

    println(numStrings.joinToString { it.uppercase() }) // ONE, TWO, THREE, FOUR
}
```

- joinTo(): Combines all the elements of a colection into a string and joins it to a string buffer[^3]

```kotlin
fun main() {
    val numStrings = listOf("one", "two", "three", "four")
    val strbuf = StringBuffer("Numbers: ")

    println(numStrings.joinTo(strbuf)) // Numbers: one, two, three, four
}
```

[^3]: In Kotlin (and Java), `StringBuffer` is a class used for creating and manipulating strings in a mutable way. It provides an efficient way to handle string operations like concatenation and modifications compared to immutable String objects.

## Collection-Specific Functions

### List Functions:

- first / last: Returns the first/last element or throws an exception if the list is empty.

- getOrNull: Returns the element at the specified index or null if the index is out of bounds.

### Set Functions:

- plus / minus: Adds or removes elements to/from the set, returning a new set.

### Map Functions:

- keys / values: Returns the set of keys or the collection of values in the map.

- entries: Returns the set of key-value pairs.