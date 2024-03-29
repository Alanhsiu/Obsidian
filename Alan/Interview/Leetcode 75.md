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
		
		string s="abc";
		reverse(s.begin(), s.end());
	```
	* Product of Array Except for Self #prefix_sum
	* String Compression
	```cpp
		#include <string>
		int num=123; std::to_string(num);
		std::string str = "1234"; int num = stoi(str);
	```
	* Others
		* <code>string d="1234"; int sub_d=d.substr(0, 2); </code> // usage: str.substr(index, length);
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
	* Time Complexity
		* set / map (red-black tree): 
			* Insertion: O(log n)
			- Search: O(log n)
			- Deletion: O(log n)
			- Traversal: O(n) (in sorted order)
		* unordered_set / unordered_map (hash table)
			* Insertion: Average O(1), Worst-case O(n)
			- Search: Average O(1), Worst-case O(n)
			- Deletion: Average O(1), Worst-case O(n)
			- Traversal: O(n) (no specific order)
	* unordered_set initialization
		* <code>set.insert()</code>
	```cpp
		unordered_set<int> set1(nums1.begin(), nums1.end())
		
		std::unordered_set<int> mySet;
	    mySet.insert(10);

		for (int x : mySet) 
			std::cout << x << " "; 
```
	* unordered_set find
		* <code>set.count()</code>
		```cpp
		if (set1.count(i) == 0) 
			temp1.push_back(i);
```

	* unordered_map iteration
		* <code>for (const auto& pair : myMap){} </code>
	```cpp
		for (const auto& pair : myMap) {
			 std::cout << "Key: " << pair.first 
			 << ", Value: " << pair.second << std::endl;
		}
	```
	* unordered_map find
		* <code>auto it = m.find(key)</code>
		```cpp
		auto it = myMap.find(key);
	    if (it != myMap.end()) {
	        std::cout << "Element with key '" << key << "' exists in the unordered map." << std::endl;
	    } else {
	        std::cout << "Element with key '" << key << "' does not exist in the unordered map." << std::endl;
	    }
    ```
	* set
	```cpp
	if (!mySet.empty()) { int minValue = *mySet.begin();}
	mySet.erase(minValue);
	```
	
* Stack 
	* <code>s.push(); s.pop(); s.size(); s.empty(); s.top()</code>
* Queue
	* <code>q.push(); q.pop();  q.empty(); q.front()</code>
* Linked List
	* <code>ListNode* nodes = new ListNode[10]; delete[] nodes;</code>
* Binary Tree - DFS
	* create extra function dfs -> recursive
* Binary Tree - BFS
	* use queue
	* vec.begin(), vec.end()
	* vec.front(), vec.back()
* Binary Search Tree
	* Delete Node in a BST: find the rightmost child among the left-child's children to replace root (if root has 2 children)
* Graph - DFS
	* use vector adj to record neighbors of each node
	* use vector vis to record if the node is visited
* Graph - BFS
	* use queue
	* <code>while(!q.empty()){int node=q.front(); q.pop(); for-loop}</code>
* Heap / Priority Queue
	* <code>pq.push(x); pq.pop(); pq.top(); pq.empty(); pq.size(); </code>
	* Time Complexity
		* push: O(log n)
		* pop: O(log n)
		* top, size, empty: O(1)
	```cpp
	std::priority_queue<int> pq; // max-heap
	priority_queue<int> pq(nums.begin(), nums.end());
	std::priority_queue<int, std::vector<int>, std::greater<int>> pq; 
	```
	* reversed sort  <code>sort(p.rbegin(), p.rend());</code>
* Binary Search
* Backtracking
* DP - 1D
* DP - Multidimensional
	* `vector<vector<int>> dp(len1, vector<int>(len2, 0));`
* Bit Manipulation
	* & ^
* Trie
* Interval
* Monotonic Stack