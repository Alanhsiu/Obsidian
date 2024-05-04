### Review Policy Gradient

* ![[Pasted image 20240503163754.png]]
* 讓 agent 與環境互動，計算在某一個 state s 採取某一個 action a 的機率。
* G 的不穩定是因為互動過程中的隨機性，為 random variable，過程中從 sample，然後用 sample 到的資料更新參數。
* 即使是相同的 state-action pair，最終得到的結果還是可能如上圖說明一般的存在很大的落差，因此我們希望可以直接估測 G 這個 random variable 的期望值，用期望值來代替 sample 的值 → value-based methods

### Review Q Learning

* ![[Pasted image 20240503164624.png]]
* TD 比較穩，MC 比較精確。

### Actor-Critic

* ![[Pasted image 20240504155108.png]]
* Q function 的定義就是 accumulated reward 的期望值，就是 G 的期望值。
* 把 Q function 套在 G 上面就可以將 actor-critic 兩個方法結合起來。
* baseline 的話，可以用 **value function** 來表示，即在 policy $\pi$ 的情況下，在某一個 state s 一直互動到遊戲結束的 expected reward 有多大 (V function 沒有考慮action，Q function 才有 action 考慮)。 