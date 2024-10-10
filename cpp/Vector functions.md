# Vectors in C++

## What is a Vector?
A vector in C++ is a dynamic array provided by the Standard Template Library (STL). It can grow or shrink in size as needed, making it a versatile and convenient data structure for managing collections of items.

## Key Features of Vectors
- **Dynamic Size**: Unlike arrays, vectors can change size dynamically.
- **Contiguous Memory**: Elements are stored in contiguous memory, which allows for efficient access.
- **Support for Various Data Types**: Vectors can store any data type, including user-defined types.

## Including Vectors
To use vectors, include the header:
```cpp
#include <vector>
```

## Commonly Used Functions

### Initialization
```cpp
std::vector<int> vec;              // Creates an empty vector of integers
std::vector<int> vec(5);           // Creates a vector with 5 default-initialized elements
std::vector<int> vec{1, 2, 3};     // Initializes a vector with specified elements
```

### Adding Elements

- push_back(value): Adds an element to the end of the vector.
```cpp
vec.push_back(4);
```

### Accessing Elements

- operator[]: Accesses elements at a specified index.
```cpp
int x = vec[0]; // Access first element
```

- at(index): Accesses elements with bounds checking [^1].
```cpp
int y = vec.at(1); // Access second element
```

### Removing Elements

- pop_back(): Removes the last element of the vector.
```cpp
vec.pop_back();
```

### Size and Capacity

- size(): Returns the number of elements in the vector.
```cpp
size_t size = vec.size();
```

- capacity(): Returns the size of the allocated storage.
```cpp
size_t cap = vec.capacity();
```

### Resizing

- resize(new_size): Changes the number of elements in the vector.
```cpp
vec.resize(10); // Resizes vector to 10 elements
```

### Iterating Over Vectors
- You can use a range-based for loop to iterate over elements:
```cpp
for (int i : vec) {
    std::cout << i << " ";
}
```

### Example

- Here’s a simple example demonstrating some vector operations:

```cpp
#include <iostream>
#include <vector>

int main() {
    // Initialization
    std::vector<int> vec;              // Creates an empty vector
    std::vector<int> vecWithSize(5);   // Creates a vector with 5 default-initialized elements
    std::vector<int> vecWithElements{1, 2, 3}; // Initializes a vector with specified elements

    // Adding Elements
    vec.push_back(4); // Adds 4 to the end of vec
    vec.push_back(5); // Adds 5 to the end of vec

    // Accessing Elements
    int firstElement = vec[0]; // Access first element
    int secondElement = vec.at(1); // Access second element with bounds checking

    // Output the accessed elements
    std::cout << "First element: " << firstElement << std::endl;
    std::cout << "Second element: " << secondElement << std::endl;

    // Removing Elements
    vec.pop_back(); // Removes the last element (5)

    // Size and Capacity
    size_t size = vec.size(); // Returns the number of elements
    size_t capacity = vec.capacity(); // Returns the allocated storage size

    // Resizing
    vec.resize(10); // Resizes vector to 10 elements (new elements are default-initialized)

    // Iterating Over Vectors
    std::cout << "Vector elements: ";
    for (int i : vec) {
        std::cout << i << " "; // Output the elements
    }
    std::cout << std::endl;

    // Final Output
    std::cout << "Size of vector: " << size << std::endl;
    std::cout << "Capacity of vector: " << capacity << std::endl;

    return 0;
}
```

- Output:

```bash
First element: 4
Second element: 5
Vector elements: 4 0 0 0 0 0 0 0 0 0 
Size of vector: 1
Capacity of vector: 2
```


[^1]: 1. Bounds Checking:
        1. operator[]: Does not perform bounds checking. If you try to access an element outside the valid range, it results in undefined behavior.
            - Example:
                ```cpp
                std::vector<int> vec{1, 2, 3};
                int x = vec[5]; // Undefined behavior if index is out of bounds
                ```
        2. at(): Performs bounds checking. If you try to access an element outside the valid range, it throws an std::out_of_range exception.
            - Example:
                ```cpp
                std::vector<int> vec{1, 2, 3};
                try {
                    int y = vec.at(5); // Throws std::out_of_range
                } catch (const std::out_of_range& e) {
                    std::cerr << "Error: " << e.what() << std::endl; // Catch the exception
                }
                ```
    2. Usage Context:
        1. operator[]: Generally used when you are confident about the index being valid or when performance is critical, and you want to avoid the overhead of exception handling.
        2. at(): Recommended when you want to ensure safety and catch potential errors due to invalid indexing, especially in cases where the index may not be guaranteed to be valid.
    3. Return Type:
    Both methods return a reference to the element at the specified index, allowing for both reading and modifying the element.