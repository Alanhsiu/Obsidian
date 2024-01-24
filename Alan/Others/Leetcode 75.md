* Array / String
	* Greatest Common Divisor of Strings
		* gcd(greatest common divisor), lcm
```cpp
#include <algorithm>
std::gcd(a, b);
std::lcm(a, b);
```
		* lib: algorithm
		* (GCD) <code>std::gcd(a, b);</code>
		* least common multiple (LCM) <code>std::lcm(a, b);</code>
	* Reverse Words in a String 
		``` cpp
		#include <sstream>
		stringstream ss(s);
		while(ss >> word){}
		```
	* Product of Array Except Self #prefix_sum

	* to_string
		* lib: string
		* <code>std::to_string(123);</code>
* Two Pointers
	* Move Zeros #two_pointers
	* Is Subsequence #dynamic_programming #two_pointers 
	* Container With Most Water: use two pointers (leftmost and rightmost) #greedy #two_pointers 
	* 