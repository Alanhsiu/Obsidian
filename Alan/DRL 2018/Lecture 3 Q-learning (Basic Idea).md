### Critic

* Q-learning 是 value-based，訓練的並不是 policy，而是 critic。critic 本身並不會有直接的行為，而是**評價現在的行為 actor($\pi$)有多好或多不好**。
* Critic 的 output 有多大取決於 state($s$) 與 actor($\pi$)，因此，**一個 critic 綁定一個 actor**，因為它衡量的是 actor 的好壞，而不是 state。
* ![[Pasted image 20240501234113.png]]

### How to estimate $V^\pi$

* Monte-Carlo (MC) based approach: 當 actor 看到 $s_t$，接下來所得到的 cumulated reward $G_t$ 有多大
* Temporal-difference (TD) approach: $V^\pi (s_t)=V^\pi (s_{t+1})+r_t$  
* Another critic: State-action value function

### Q-learning Tips

* Fix "Target Network", after updating N times, replace it with current network.
* Exploration
	* 給定一個 state，看哪一個 action 得到的 Q value 最大就採用它
	* 問題：其他 action 就永遠不會採用到了
	* ![[Pasted image 20240502001153.png]]
* Replay Buffer
	* 裡面存的可能是由不同的 $\pi$ (policy) 得到的結果
	* 可以減少搜集資料的時間，每次隨機從裡面拿出一個 batch 拿出來 update Q
	* 一個 batch 裡面的資料比較 diverse (比較好)
	* ![[Pasted image 20240502001453.png]]
* Q-learning Algorithm
	* ![[Pasted image 20240502002037.png]]