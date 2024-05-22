* The agent learned and the agent interacting with the environment is
	* the same: On-policy (自己玩自己學) → policy gradient
	* different: Off-policy (旁邊看別人玩)
* **Off-policy**
	* 用同一筆 data (另一個 agent 搜集的) 執行 gradient ascent 很多次
	* **Importance Sampling**: 從 q 裡面 sample (q 是從 p 這個 distribution 做 sample )
	* Importance Sampling Issue: $p_\theta$ 和 $p_ {\theta '}$ 分佈不能差太多，解決方法為 PPO
*  PPO
	* 多加一個 constraint 到最佳化式子：$KL(\theta ,{\theta '})$
	* TRPO (Trust Region Policy Optimization)：當成額外的 constraint
	* KL divergence: $KL(\theta ,{\theta '})$ 指得是「行為上的距離」(action 的分佈)而不是「參數上的距離」
	* ![[Pasted image 20240502094044.png]]
* [ChatGPT] PPO（Proximal Policy Optimization，近端策略優化）是一種在強化學習（Reinforcement Learning，RL）中常用的策略優化算法，由OpenAI在2017年提出。PPO算法以其簡單、高效和穩定的優化過程而聞名。

	### 主要概念

	1. **策略（Policy）**：在強化學習中，策略是指從狀態到動作的映射，表示在某一狀態下應該採取什麼動作。
	2. **價值函數（Value Function）**：用來估計某一狀態的價值，即從這個狀態開始，未來可能獲得的總回報。

	### PPO的特點
	
	PPO主要通過限制策略更新的幅度來穩定訓練過程，具體方法如下：
	
	1. **目標函數**：PPO使用一個被稱為「剪切目標函數」（Clipped Objective Function）的目標函數，限制新策略與舊策略之間的變化幅度，避免過大的更新。
	    
	2. **信任域（Trust Region）**：與Trust Region Policy Optimization（TRPO）類似，PPO試圖在策略更新時保持在一個信任域內，但PPO的計算更加簡單，避免了複雜的二次規劃。
	    
	3. **剪切操作（Clipping）**：PPO通過剪切機制來約束策略的變化，具體是將策略更新限制在一定範圍內，防止策略變化過大導致的不穩定。
	    
	### PPO算法步驟
	
	1. **收集樣本**：根據當前策略與環境互動，收集一批樣本（狀態、動作、回報）。
	2. **計算優勢估計（Advantage Estimation）**：根據收集到的樣本計算每一步的優勢函數值，這裡可以使用Generalized Advantage Estimation（GAE）。
	3. **更新策略**：根據剪切目標函數，利用梯度上升法或梯度下降法更新策略參數。
	4. **重複上述步驟**：迭代進行上述步驟直到收斂或達到預定的訓練次數。
	
	### 總結
	
	PPO通過簡單有效的方式限制策略更新幅度，平衡了探索和利用，使得訓練過程更加穩定和高效。由於其易於實現和良好的性能，PPO在各種強化學習任務中被廣泛應用。