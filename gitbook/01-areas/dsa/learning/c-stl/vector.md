### Overview

A vector is a dynamic array in C++, also known as a sequence container. It allows for dynamic resizing, which means that elements can be added or removed from the vector after it has been created. Vectors are part of the C++ Standard Template Library (STL) and are widely used due to their flexibility and efficiency.

### Ways to initialize

There are multiple ways to initialize a vector in C++. You can use constructor initialization, brace initialization, or use the assignment operator with another vector.

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    // Constructor initialization
	vector<int> vec(5); // Creates a vector of size 5 with all elements initialized to 0
    vector<int> vec1(5, 10); // Creates a vector of size 5 with all elements initialized to 10

    // Brace initialization
    vector<int> vec2 = {1, 2, 3, 4, 5};

    // Copy initialization
    vector<int> vec3(vec2);

    return 0;
}
```

### Member functions

Iterators

1. **[begin()](https://www.geeksforgeeks.org/vectorbegin-vectorend-c-stl/)** – Returns an iterator pointing to the first element in the vector
2. **[end()](https://www.geeksforgeeks.org/vectorbegin-vectorend-c-stl/)** – Returns an iterator pointing to the theoretical element that follows the last element in the vector
3. **[rbegin()](https://www.geeksforgeeks.org/vector-rbegin-and-rend-function-in-c-stl/)** – Returns a reverse iterator pointing to the last element in the vector (reverse beginning). It moves from last to first element
4. **[rend()](https://www.geeksforgeeks.org/vector-rbegin-and-rend-function-in-c-stl/)** – Returns a reverse iterator pointing to the theoretical element preceding the first element in the vector (considered as reverse end)
5. **[cbegin()](https://www.geeksforgeeks.org/vector-cbegin-vector-cend-c-stl/)** – Returns a constant iterator pointing to the first element in the vector.
6. **[cend()](https://www.geeksforgeeks.org/vector-cbegin-vector-cend-c-stl/)** – Returns a constant iterator pointing to the theoretical element that follows the last element in the vector.
7. **[crbegin()](https://www.geeksforgeeks.org/vectorcrend-vectorcrbegin-examples/)** – Returns a constant reverse iterator pointing to the last element in the vector (reverse beginning). It moves from last to first element
8. **[crend()](https://www.geeksforgeeks.org/vectorcrend-vectorcrbegin-examples/)** – Returns a constant reverse iterator pointing to the theoretical element preceding the first element in the vector (considered as reverse end)

Capacity

1. **[size()](https://www.geeksforgeeks.org/vectorempty-vectorsize-c-stl/)** – Returns the number of elements in the vector.
2. **[max_size()](https://www.geeksforgeeks.org/vector-max_size-function-in-c-stl/)** – Returns the maximum number of elements that the vector can hold.
3. **[capacity()](https://www.geeksforgeeks.org/vector-capacity-function-in-c-stl/)** – Returns the size of the storage space currently allocated to the vector expressed as number of elements.
4. **[resize(n)](https://www.geeksforgeeks.org/vector-resize-c-stl/)** – Resizes the container so that it contains ‘n’ elements.
5. **[empty()](https://www.geeksforgeeks.org/vectorempty-vectorsize-c-stl/)** – Returns whether the container is empty.
6. **[shrink_to_fit()](https://www.geeksforgeeks.org/vector-shrink_to_fit-function-in-c-stl/)** – Reduces the capacity of the container to fit its size and destroys all elements beyond the capacity.
7. **[reserve()](https://www.geeksforgeeks.org/using-stdvectorreserve-whenever-possible/)** – Requests that the vector capacity be at least enough to contain n elements.

Element access

1. **[reference operator [g]](https://www.geeksforgeeks.org/vectoroperator-vectoroperator-c-stl/)** – Returns a reference to the element at position ‘g’ in the vector
2. **[at(g)](https://www.geeksforgeeks.org/vectorat-vectorswap-c-stl/)** – Returns a reference to the element at position ‘g’ in the vector
3. **[front()](https://www.geeksforgeeks.org/vectorfront-vectorback-c-stl/)** – Returns a reference to the first element in the vector
4. **[back()](https://www.geeksforgeeks.org/vectorfront-vectorback-c-stl/)** – Returns a reference to the last element in the vector
5. **[data()](https://www.geeksforgeeks.org/vector-data-function-in-c-stl/)** – Returns a direct pointer to the memory array used internally by the vector to store its owned elements.

**Modifiers**

1. **[assign()](https://www.geeksforgeeks.org/vector-assign-in-c-stl/)** – It assigns new value to the vector elements by replacing old ones
2. **[push_back()](https://www.geeksforgeeks.org/vectorpush_back-vectorpop_back-c-stl/)** – It push the elements into a vector from the back
3. **[pop_back()](https://www.geeksforgeeks.org/vectorpush_back-vectorpop_back-c-stl/)** – It is used to pop or remove elements from a vector from the back.
4. **[insert()](https://www.geeksforgeeks.org/vector-insert-function-in-c-stl/)** – It inserts new elements before the element at the specified position
5. **[erase()](https://www.geeksforgeeks.org/vectorclear-vectorerase-c-stl/)** – It is used to remove elements from a container from the specified position or range.
6. **[swap()](https://www.geeksforgeeks.org/vectorat-vectorswap-c-stl/)** – It is used to swap the contents of one vector with another vector of same type. Sizes may differ.
7. **[clear()](https://www.geeksforgeeks.org/vectorclear-vectorerase-c-stl/)** – It is used to remove all the elements of the vector container
8. **[emplace()](https://www.geeksforgeeks.org/vector-emplace-function-in-c-stl/)** – It extends the container by inserting new element at position
9. **[emplace_back()](https://www.geeksforgeeks.org/vectoremplace_back-c-stl/)** – It is used to insert a new element into the vector container, the new element is added to the end of the vector

`push_back()` vs `emplace_back()` :

Both `push_back` and `emplace_back` are member functions of the `std::vector` class in C++, used to add elements to the end of the vector. However, they have some key differences:

1. **Argument types**:
    - `push_back`: Accepts a copy of the element to be added.
    - `emplace_back`: Accepts constructor arguments for the element to be constructed in place.
2. **Copying/moving**:
    - `push_back`: Copies or moves the given element into the vector. If the element is already constructed elsewhere, it will be copied or moved into the vector.
    - `emplace_back`: Constructs the element in place at the end of the vector, using the provided arguments. This can avoid unnecessary copies or moves, especially when dealing with complex types or expensive-to-copy/move elements.
3. **Performance**:
    - `push_back`: May involve additional copying or moving of the element, depending on its type and whether it's already constructed elsewhere.
    - `emplace_back`: Typically more efficient than `push_back` because it constructs the element directly in the vector's memory, avoiding unnecessary copying or moving.

Here's a quick example to illustrate the difference:

```cpp
#include <iostream>
#include <vector>
#include <string>
using namespace std;

class MyObject {
public:
    MyObject(const string& s) : data(s) {
        cout << "Constructor called: " << data << endl;
    }
private:
    string data;
};

int main() {
    vector<int> vec1;
    vec1.push_back(10); // Copies the integer 10 into the vector

    vector<MyObject> vec2;
    vec2.emplace_back("hello"); // Constructs MyObject in place in the vector

    return 0;
}
```

In this example, when using `push_back`, the integer `10` is copied into the vector `vec1`. However, when using `emplace_back`, a `MyObject` is constructed in place within `vec2` using the provided constructor arguments `"hello"`. This avoids unnecessary copies and can be more efficient, especially for complex types.

The time complexity for doing various operations on vectors is-

- Random access – constant O(1)
- Insertion or removal of elements at the end – constant O(1)
- Insertion or removal of elements – linear in the distance to the end of the vector O(N)
- Knowing the size – constant O(1)
- Resizing the vector- Linear O(N)

### Operators

- `[]` : Accesses the element at the specified index. (Constant time complexity)
- `==` : Compares two vectors for equality, element by element. (Linear time complexity)
- `!=` : Compares two vectors for inequality, element by element. (Linear time complexity)

### Insertion

- `.insert(iterator, val)` : Inserts a new element with value `val` before the element at the specified iterator position. (Linear time complexity)
- `.emplace(iterator, args...)` : Constructs a new element in place at the specified iterator position, using the provided arguments. (Linear time complexity)

### Modification

- You can modify elements of a vector directly by accessing them using the `[]` operator or iterator.

### Deletion

- `.erase(iterator)` : Removes the element at the specified iterator position. (Linear time complexity)
- `.clear()` : Removes all elements from the vector. (Linear time complexity)

### Search

- `.find(val)` : Searches for the first occurrence of `val` in the vector and returns an iterator to it. If `val` is not found, returns `end()`. (Linear time complexity)

### Traversal

- Vectors can be traversed using iterators, range-based for loops, or traditional for loops. (Linear time complexity)

### Competitive coding question example

Question: **[Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)** Description: Given an integer array `nums`, return true if any value appears at least twice in the array, and return false if every element is distinct.

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>
using namespace std;

bool containsDuplicate(vector<int>& nums) {
    unordered_set<int> seen;

    for (int num : nums) {
        if (seen.find(num) != seen.end()) {
            return true;
        }
        seen.insert(num);
    }

    return false;
}

int main() {
    vector<int> nums = {1, 2, 3, 1};

    if (containsDuplicate(nums)) {
        cout << "Duplicates found\\\\n";
    } else {
        cout << "No duplicates found\\\\n";
    }

    return 0;
}
```

Explanation: In this problem, a vector is used to store the elements of the array. By using an unordered set to keep track of seen elements, you can efficiently determine if there are any duplicates in the array.