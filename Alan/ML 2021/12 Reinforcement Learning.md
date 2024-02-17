* 應用場景
	* 給機器一個輸入，但**我們不知道最佳輸出為何**
	* 收集有標註的資料有難度
* 角色
	* Actor和Environment進行互動
	* Actor就是RL中要找的function
		* 輸入: observation (from environment)
		* 輸出: action (to environment)
		* 目標: 最大化reward總和 (from environment)
	
			![[Pasted image 20240217202912.png]]

* 訓練三步驟
	1. Function with Unknown
		* **Actor = Policy Network**
		* 架構：FC, CNN, Transformer
		* 輸入：遊戲畫面的pixels
		* 輸出：每個可採取行為的分數（總和為1）
	2. Define "Loss"
		* 1局遊戲 = 1個 episode
		* Reward：每個行為得到的反饋
		* Return：整場遊戲得到的 total reward
		* Loss：**-R** (to maximize return)
	3. Optimization
		* 對環境的 observation $s_1$，會變成 actor 的輸入，actor 依此輸出 action $a_1$，$a_1$又作為環境的輸入，根據 $a_1$ 輸出 $s_2$，以此類推，直至滿足遊戲終止條件
		* s 跟 a 所形成的 sequence $\{s_1,a_1,s_2,a_2,...\}$ 稱作 **Trajectory**，以 $\tau$ 表示
		* **Reward 的輸入是 observation + action。**
		* ![[Pasted image 20230927211259.png]]
	* 目標：找到 actor 的一組參數，使得 $R(\tau)$ 越大越好
	* 問題：
		* actor (network) 具有隨機性：由於 action 是 sample 產生的，給定相同的 s，產生的 a 可能不一樣
		* environment 和 reward 是黑盒子：environment 和 reward 都不是 network，也都具有隨機性
* Optimization: **Policy Gradient**
	* 如何控制 Actor
		* 若希望 actor 在看到某個 s 時採取某一 action，只需將其看做一般的分類問題即可，為其設定 ground truth $\hat{a}$， loss e 採用 **cross-entropy**
		* 若希望 actor 在看到某個 s 時不採取某一 action，只需將 cross-entropy 乘一個負號，最小化 L 等同於最大化 e，以使 actor 的 action 離 $\hat{a}$ 更遠
		* 綜合以上兩種情況，可將 L 定義為 $e_1-e_2$，找到一組參數最小化 $e_1$，同時最大化 $e_2$，即可最小化 loss L
	* 收集訓練資料
		* 為每個行為標註為”好”或”不好”（+1、-1）
		* 每個行為給定一個分數$A_n$ (不再是只有正負 1)
	* 如何定義 A
		* Version 0 （不正確）：**一直開火**。將 reward 作為 A 用於定義 loss → 短視近利
		* Version 1（Cumulated Reward）：**把這個動作之後的reward全部加起來**。假設遊戲非常長，把 $r_N$ 歸功於 $a_1$ 也不合適
		* Version 2（Discounted Cumulated Reward）：新增 discount factor $\gamma$（$\gamma$<1），離 $a_t$ 比較近的 reward 給予較大的權重，較遠的 reward 給予較小的權重，使較遠的 reward 影響較小
		* Version 3（標準化：-b）：假設某一遊戲得到的 reward 永遠都是正的，只是有大有小不同，因此每個 G 都會是正的，就算某些行為是不好的，還是會鼓勵機器採取某些行為
		* Version 3.5（b = value function）：訓練一個 critic，給一個 observation s，輸出 $V^\theta(s)$，讓 Version 3 的 b = $V^\theta(s)​$  
		* Version 4（Advantage Actor-Critic）：在 observation $s_t$ 下，採取 action $a_t$ 到 $s_{t+1}$，考慮在 $s_{t+1}$ 下採取各種 action $a_{t+1}$ 的情况，並求所有 $G'_{t+1}$ 的平均值（期望值）。因為 **value function 意義上可以代表各種 action 的平均 discounted cumulated reward**，因此直接使用 $V^\theta(s_{t+1})$ 表示 $s_{t+1}$下各種 $a_{t+1}$ 得到的 $G'_{t+1}$的平均值（期望值），所以將 $G'_{t}$ 替換為 $r_t+V^\theta(s_{t+1})$ ⇒ $A_t=r_t+V^\theta(s_{t+1})-V^\theta(s_{t})$
	* 訓練過程
		1. 隨機初始化 actor，參數為 $\theta^0$
		2. 迭代更新 actor：用參數為 $\theta^{i-1}$ 的 actor 蒐集資料，並以此資料計算 $A$，再計算 loss $L$，做 gradient descent 更新參數
		* On-policy Learning：訓練的 actor 跟與環境互動的 actor 是同一個
		* Off-policy Learning：訓練的 actor 跟與環境互動的 actor 是不同的 好處是不用一直收集資料，可以用一次收集到的資料，更新多次 actor
			* eg. PPO (Proximal Policy Optimization) The *actor to train* has to know its difference from the *actor to interact*
			* Exploration（增加 actor 做 action 的隨機性）
* Critic
	* Value Function：有一 actor 參數為 $\theta$，當前的 observation 為 s，value function $V^\theta(s)$ 為基於參數為 $\theta$ 的 actor 及 observation s，所預期的 discounted cumulated reward (期望值的概念）
	* How to train critic
		* Monte Carlo（MC） Based Approach：將 actor 拿去跟環境互動很多輪（episodes），得到一些遊戲的記錄（訓練資料）
		* Temporal-Difference（TD） Approach：不需玩完整場遊戲（一個 episode）得到訓練資料。只要在看到 observation $s_t$， actor 執行 action $a_t$，得到 reward $r_t$，接下來再看到 observation $s_{t+1}$，就能夠更新一次 critic 參數。此方法對於很長的遊戲或玩不完的遊戲非常合適
	* Deep Q Network（DQN）https://youtu.be/o_g9JUMw1Oc
* Reward Shaping
	* Sparse Reward
		* 問題： Sparse Reward 就是 reward 大多數情況都是 0，只有在少數情況是一個非常大的數值。意味著很多 actions 無從判斷是好是壞。例如圍棋到遊戲結束才會有 reward，過程中都沒有 reward。
		* 解決：Reward Shaping 定義一些額外的 reward 來幫助 actor 學習。
	* Curiosity
		* Curiosity-based reward shaping
		* 基於好奇心，讓 actor 看到有意義的新東西時獲得 reward
* No Reward： Imitation Learning
	* 問題：
		* 遊戲中雖然容易定義 reward，但在其他任務要定義 reward 很困難
		* 人工設置一些 reward（reward shaping）教機器學時，若 reward 沒設定好，機器可能會產生奇怪、無法預期的行為
	* 解決：沒有 reward 的狀況下，可使用 imitation learning
	* Imitation Learning：在沒有 reward 的情況下訓練 actor
		* 引入 expert（通常為人類）的示範。找很多 experts 跟環境互動，記錄互動的結果 $\hat{\tau}$，每個 $\hat{\tau}$ 代表一個 trajectory
	* Behavior Cloning：類似於監督式學習，讓機器做出的 action 跟 export 做出的 action 越接近越好，又稱作 Behavior Cloning
	* Inverse Reinforcement Learning：從 expert 的 demonstration，還有 environment 去反推 reward function，學出一個 reward function 後，再用一般的 RL 來訓練 actor
* 三種方法
	* Policy - Actor-Critic - DQN