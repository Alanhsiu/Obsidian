### Critic
* Q-learning 是 value-based，訓練的並不是 policy，而是 critic。critic 本身並不會有直接的行為，而是**評價現在的行為 actor($\pi$)有多好或多不好**。
* Critic 的 output 有多大取決於 state($s$) 與 actor($\pi$)，因此，**一個 critic 綁定一個 actor**，因為它衡量的是 actor 的好壞，而不是 state。
* Monte-Carlo (MC) based approach: 當 actor 看到 $s_t$，接下來所得到的 cumulated reward $G_t$ 有多大
* Temporal-difference (TD) approach: $V^\pi (s_t)=V^\pi (s_{t+1})+r_t$  
* State-action value function
* ![[Pasted image 20240501234113.png]]