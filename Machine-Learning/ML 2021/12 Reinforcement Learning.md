* 應用場景
	* 給機器一個輸入，但我們不知道最佳輸出為何
	* 收集有標註的資料有難度
* 角色
	* Actor和Environment進行互動
	* Actor就是RL中要找的function
		* 輸入: observation (from environment)
		* 輸出: action (to environment)
		* 目標: 最大化reward總和 (from environment)
* 訓練三步驟
	1. Function with Unknown
		* Actor = Policy Network
		* 架構：FC, CNN, Transformer
		* 輸入：遊戲畫面的pixels
		* 輸出：每個可採取行為的分數（總和為1）
	2. Define "Loss"
		* 1局遊戲 = 1個episode
		* Reward：每個行為得到的反饋
		* Return：整場遊戲得到的reward總和
		* Loss：**-R** (to maximize return)
	3. Optimization
		* 對環境的 observation $s_1$，會變成 actor 的輸入，actor 依此輸出 action $a_1$，$a_1$又作為環境的輸入，根據 $a_1$ 輸出 $s_2$，以此類推，直至滿足遊戲終止條件
		* s 跟 a 所形成的 sequence $\{s_1,a_1,s_2,a_2,...\}$ 稱作 **Trajectory**，以 $\tau$ 表示
		* ![[Pasted image 20230927211259.png]]
	* 目標：找到 actor 的一組參數，使得 $R(\tau)$ 越大越好
	* 問題：
		* actor 具有隨機性：由於 action 是 sample 產生的，給定相同的 s，產生的 a 可能不一樣
		* environment 和 reward 是黑盒子：environment 和 reward 都不是 network，也都具有隨機性
* Optimization: Policy Gradient
	* 