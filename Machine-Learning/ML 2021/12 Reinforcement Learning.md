* 應用場景
	* 給機器一個輸入，但我們不知道最佳輸出為何
	* 收集有標註的資料有難度
* 角色
	* Actor和Environment進行互動
	* Actor就是RL中要找的function
		* input: observation (from environment)
		* output: action (to environment)
		* objective: 最大化reward總和 (from environment)
* 訓練三步驟
	1. Function with Unknown
	2. Define "Loss"
	3. Optimization