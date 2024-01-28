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
	* iteration
	```cpp
		for (const auto& pair : myMap) {
			 std::cout << "Key: " << pair.first 
			 << ", Value: " << pair.second << std::endl;
		}
	```
	* check if exists an element
		```cpp
		auto it = myMap.find(key);
	    if (it != myMap.end()) {
	        std::cout << "Element with key '" << key << "' exists in the unordered map." << std::endl;
	    } else {
	        std::cout << "Element with key '" << key << "' does not exist in the unordered map." << std::endl;
	    }
    ```
    