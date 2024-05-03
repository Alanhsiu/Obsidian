### Review Policy Gradient

* ![[Pasted image 20240503163754.png]]
* 讓 agent 與環境互動，計算在某一個 state s 採取某一個 action a 的機率。
* G 的不穩定是因為互動過程中的隨機性，為 random variable，過程中從 sample，然後用 sample 到的資料更新參數。
* 即使是相同的 state-action pair，最終得到的結果還是可能如上圖說明一般的存在很大的落差，因此我們希望可以直接估測 G 這個 random variable 的期望值，用期望值來代替 sample 的值 → value-based methods

### Review Q Learning

* ![[Pasted image 20240503164624.png]]
* TD 比較穩，MC 比較精確。

### Actor-Critic

* 