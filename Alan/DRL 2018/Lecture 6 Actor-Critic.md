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
* ![[Pasted image 20240504155957.png]]
* 將 G 取代掉的部份稱為 **Advantage function**
* Steps
	1. 初始的 actor $\pi$，與環境互動收集資料
	2. 不同於 Policy Gradient 直接更新參數，是利用收集到的資料來估測 value function （可以使用 TD 或 MC）
	3. 用新的 value function 去 update $\pi$
* Tips
	* ![[Pasted image 20240504160625.png]]
	* 訓練過程中有兩個 nn，一個是 V function，一個是 Policy (actor)。其中 V function input state，output scalar。actor 的話是 input state，output action 的distribution。因為兩個 nn 的 input 都是 state，因此前面幾個 layer 的話是可以共用的。如果是影像的輸入的話，就可以將輸入的像素轉為較高階的資訊。
	* 一樣需要 exploration 的機制，實作 Actor-Critic 的一種常見作法，就是對 actor 的 output(action distribution)多一個 constraint，讓 distribution 的 entropy 不要太小，探索更好的結果。
* Asynchronous Advantage Actor-Critic (A3C)
	* 鳴人用影分身訓練自己，最後再集合經驗。
	* 同時開很多 Worker，做完就回傳參數，即使「原本取到的參數」和「回傳時的參數」不一樣也沒有關係，一樣直接用$\nabla \theta$更新。
* Pathwise derivative policy gradient
	* Critic 不只跟 actor 說這個動作好不好，還告訴 actor 應該要採取什麼動作。
	* 概念跟 GAN 非常相似，將 Q 視為 discriminator，要依據 discriminator 決定 action 非常困難，那就另外 learn 一個 nn 來解這個問題，也就是 actor (generator)，利用 actor 來決定 action，解 argmax 的問題。
	* ![[Pasted image 20240504162426.png]]
	* 原本是用 Q function 決定採用那一個 action，調整為直接用 actor 來決定，不需要再解 argmax 的問題。

