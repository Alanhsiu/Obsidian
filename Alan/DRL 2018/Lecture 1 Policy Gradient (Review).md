* [note link](https://hackmd.io/@shaoeChen/Bywb8YLKS/https%3A%2F%2Fhackmd.io%2F%40shaoeChen%2FHkH2hSKuS)
* Basic Component: Actor, Env, Reward
* Policy Gradient
	* Env, Reward Function 是固定的
	* 只有 Actor 可以調整 Policy
	* Trajectory: {s1, a1, s2, a2, ...}
* Tips
	* Add a Baseline: 讓 reward 有正有負
	* 如果 reward 皆為正，可能會遇到的問題是有些action沒有被sample到，
	* ![[Pasted image 20240428190526.png]]
	* Assign Suitable Credit: 加入係數 gamma，來減少對後面 action 所得的 reward 的影響