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
	* ![[Pasted image 20240501230211.png]]