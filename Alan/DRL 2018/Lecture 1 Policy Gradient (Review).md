* [note link](https://hackmd.io/@shaoeChen/Bywb8YLKS/https%3A%2F%2Fhackmd.io%2F%40shaoeChen%2FHkH2hSKuS)
* Basic Component: Actor, Env, Reward
* Policy Gradient
	* Env, Reward Function 是固定的
	* 只有 Actor 可以調整 Policy
	* Trajectory: {s1, a1, s2, a2, ...}
* Tips
	* Add a Baseline: 讓 reward 有正有負
		* 如果 reward 皆為正，可能會遇到的問題是有些 action 沒有被 sample 到，這樣相當於機率下降。
		* ![[Pasted image 20240428190722.png]]
	* Assign Suitable Credit: 加入係數 gamma，來減少對後面 action 所得的 reward 的影響
		* 整場遊戲的結果是好的，不代表每一步都是好的。
		* 理論上如果 sample 數量夠多，這樣就可以避免這個問題。（但不可能全部 sample 到）
		* 這個 action 會影響的，是執行後到遊戲結束前的東西。前面的東西跟這個 action 沒有關。
		* 離越遠的 action，和現在的 reward 就越沒關係。
		* A: 在某個 state 下，執行某個 action 有多好（相較於其他 action）
		* ![[Pasted image 20240428191450.png]]