
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
	* OOP
		* **Abstraction**：在設計複雜系統時，**抽象**是一種減少複雜性並隱藏非關鍵細節的方法，從而使開發者可以專注於互動的高層次結構。
		* **Encapsulation**：**封裝**是將數據（屬性）和操作數據的代碼（方法）包裹在一起的技術，以保護數據免受外部干擾和不當使用。
		* **Inheritance**：**繼承**是一種使得一個類（子類）能夠獲得另一個類（父類）的屬性和方法的機制，這種方式支持代碼的重用並建立一個類的層次體系。
		* **Polymorphism**：**多態**是一種允許不同類的對象通過同一個接口表現出不同行為的特性，它使接口的一般化設計成為可能，提高了程序的靈活性。
		* 「基底類別」可以定義和實作『虛擬』屬性和方法（**virtual**）。
		* 「衍生類別」可以覆寫「基底類別」的『虛擬』屬性和方法（**override**）。
* Alpha
	* In BRAIN platform, an 'Alpha' refers to a mathematical model or strategy, written as an expression, which places different bets (weights) on different instruments (stocks), and is expected to be profitable in the long run. After a user enters an Alpha expression that consists of data, operators and constants, the input code is evaluated for each instrument to construct a portfolio. Then BRAIN platform makes investments in each instrument for a one-day period in proportion to the values of the expression. The process repeats each day.
	* 在BRAIN平台中，「Alpha」指的是一個數學模型或策略，以表達式的形式書寫，對不同的工具（股票）進行不同的投注（權重），並期望從長遠來看能夠盈利。用戶輸入一個包含數據、運算符和常數的Alpha表達式後，輸入代碼將針對每個工具進行評估，以構建投資組合。然後BRAIN平台根據表達式的值，按比例對每個工具進行為期一天的投資。這個過程每天重複一次。
* 面試問題
	* T Test
	* R Square
		* 將 n 個點 double，R Square 不會變
