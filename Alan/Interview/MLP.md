
* **Pandas**
	* https://www.learncodewithmike.com/2020/11/python-pandas-dataframe-tutorial.html
* **C++**
	* `static` 變數是一種特殊的變數，它在程序執行的生命周期中只被初始化一次，其值在函數調用之間保持不變。
	* ```#include <iostream>
		using namespace std;
		void counterFunction() {
		    static int counter = 0; // 初始化一次
		    counter++;
		    cout << "Counter: " << counter << endl;
		}
		int main() {
		    counterFunction(); // 輸出: Counter: 1
		    counterFunction(); // 輸出: Counter: 2
		    counterFunction(); // 輸出: Counter: 3
		    return 0;
		}
	* 
