* The agent learned and the agent interacting with the environment is
	* the same: On-policy (自己玩自己學) → policy gradient
	* different: Off-policy (旁邊看別人玩)
* Off-policy
	* 用同一筆 data (另一個 agent 搜集的) 執行 gradient ascent 很多次
	* Importance Sampling: 從 q 裡面 sample (q 是從 p 這個 distribution 做 sample )
	* Importance Sampling Issue: $p_\theta$ 和 $p_ {\theta '}$ 分佈不能差太多，解決方法為 PPO
*  PPO 
