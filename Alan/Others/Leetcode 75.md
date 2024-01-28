* Array / String
	* Greatest Common Divisor of Strings
		* gcd (greatest common divisor), lcm (least common multiple)
	```cpp
		#include <algorithm>
		std::gcd(a, b);
		std::lcm(a, b);
	```
	* Reverse Words in a String 
	```cpp
		#include <sstream>
		stringstream ss(s);
		while(ss >> word){}
	```
	* Product of Array Except Self #prefix_sum
	* String Compression
	```cpp
		#include <string>
		int num=123;
		std::to_string(num);
	```

* Two Pointers
	* Move Zeros #two_pointers
	* Is Subsequence #dynamic_programming #two_pointers 
	* Container With Most Water: use two pointers (leftmost and rightmost) #greedy #two_pointers 
	* Max Number of K-Sum Pairs #sorting #two_pointers 
* Sliding Window
	* Max Consecutive Ones III #sliding_window
	* Longest Subarray of 1's After Deleting One Element #sliding_window 
* Prefix Sum
* Hash Map / Set
	* 記得複習複雜度
	* unordered_set initialization
	```cpp
		unordered_set<int> set1(nums1.begin(), nums1.end())
		
		std::unordered_set<int> mySet;

	    // Insert elements
	    mySet.insert(10);
	    mySet.insert(20);
	    mySet.insert(30);

		for (int x : mySet) { 
			std::cout << x << " "; 
		}
```
	* unordered_set find
		```cpp
		if (set1.count(i) == 0) {
			temp1.push_back(i);
		}
```

	* unordered_map iteration
	```cpp
		for (const auto& pair : myMap) {
			 std::cout << "Key: " << pair.first 
			 << ", Value: " << pair.second << std::endl;
		}
	```
	* unordered_map find
		```cpp
		auto it = myMap.find(key);
	    if (it != myMap.end()) {
	        std::cout << "Element with key '" << key << "' exists in the unordered map." << std::endl;
	    } else {
	        std::cout << "Element with key '" << key << "' does not exist in the unordered map." << std::endl;
	    }
    ```
    