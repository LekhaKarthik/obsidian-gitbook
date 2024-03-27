### Overview

A pair is a simple data structure in C++ that allows you to store two objects together as a single unit. It's part of the C++ Standard Template Library (STL) and can be quite handy when you need to associate two values together.
### Ways to initialize

There are multiple ways to initialise a pair in C++. You can use the constructor directly, make_pair function, or brace initialisation.

```cpp
#include <iostream> 
#include <utility> // for pair and make_pair 
using namespace std; 
int main() { 
	// Using constructor directly 
	pair<int, int> p1(1, 2); 
	
	// Using make_pair function 
	pair<int, int> p2 = make_pair(3, 4); 
	
	// Using brace initialization 
	pair<int, int> p3 = {5, 6}; 
	
	return 0; 
}
```
### Member functions
- `.first` : Access the first element of the pair.
- `.second` : Access the second element of the pair.
- `.swap()` : Swaps the contents of two pairs.
- `.make_pair()` : Constructs a pair object with its elements initialized to specific values.
- `.tie()` : Creates a tuple of lvalue references to its arguments or elements in the pair.
### Operators
- `==` : Compares two pairs for equality.
- `!=` : Compares two pairs for inequality.
- `<` : Lexicographically compares two pairs.
- `<=` : Lexicographically compares two pairs.
- `>` : Lexicographically compares two pairs.
- `>=` : Lexicographically compares two pairs.

For pairs of fundamental types like `pair<int, int>`, the operators compare the first elements first. If the first elements are equal, then the second elements are compared.

- For example, if you have two pairs `(a, b)` and `(c, d)`:
    - `==` : Returns true if `a == c` and `b == d`.
    - `<` : Returns true if `a < c` or (`a == c` and `b < d`).
    - `<=` : Returns true if `a <= c` and `b <= d`.
    - `>` : Returns true if `a > c` or (`a == c` and `b > d`).
    - `>=` : Returns true if `a >= c` and `b >= d`.

### Insertion
Pairs are typically not used for insertion, as they are fixed-size containers.
### Modification
You can modify the values of a pair directly by assigning new values to `.first` and `.second`.
### Deletion
Pairs are typically not used for deletion, as they are fixed-size containers.
### Search
Pairs are typically not used for search operations, as they are not suitable for that purpose.
### Traversal
Traversal through a pair is straightforward using the `.first` and `.second` member variables.
### Competitive coding question example
Question: [Two Sum](https://leetcode.com/problems/two-sum/) 
Description: Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`. You may assume that each input would have exactly one solution, and you may not use the same element twice. You can return the answer in any order.

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;

vector<int> twoSum(vector<int>& nums, int target) {
    unordered_map<int, int> seen;
    vector<int> result;

    for (int i = 0; i < nums.size(); ++i) {
        int complement = target - nums[i];
        if (seen.find(complement) != seen.end()) {
            result.push_back(seen[complement]);
            result.push_back(i);
            break;
        }
        seen[nums[i]] = i;
    }

    return result;
}

int main() {
    vector<int> nums = {2, 7, 11, 15};
    int target = 9;

    vector<int> indices = twoSum(nums, target);
    cout << "Indices: " << indices[0] << ", " << indices[1] << endl;

    return 0;
}

```

Explanation: Here, a pair can be used to store the index of each element along with the element itself. By iterating through the array and storing the element's index in a hash map, you can easily find the complement for each element and return the indices where the sum equals the target.
