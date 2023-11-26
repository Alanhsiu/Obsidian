
* Harvard Architecture
	* 將儲存**程序指令**和**數據**的記憶體分開。
	* CPU可以同時從兩個分開的匯流排讀取指令和數據，允許在同一個時鐘週期內進行指令讀取和數據操作，增加了處理速度。
	* Von Neumann Architecture：使用**同一個記憶體和匯流排**來儲存指令和數據。（現代電腦主要採用）
* CISC
	* 通過單一指令完成多步操作。
* RISC (Reduced Instruction Set Computer)
	* Limited and simple instruction set: fixed instruction format / **fixed instruction execution time**.
	* Large number of **general purpose registers**.
	* Emphasis on optimizing the **instruction pipeline**: increasing the processor clock frequency.
* RISC vs CISC
	* Many design borrow from both philosophies.
	* Not clear cut.
