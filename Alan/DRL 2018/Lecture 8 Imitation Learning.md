
### Introduction

* 如果今天連 Reward 都沒有，那該如何處理?
* 又稱為 learning by demonstration，或稱 apprenticeship(學徒) learning。
* 現實上難以定義 reward，但是可以收集很多人、專家的範例，那就可以考慮使用 imitation learning。
* 有兩種方法：Behavior Cloning, Inverse Reinforcement learning(inverse optimal control)。

### Behavior Cloning

* 與 supervised learning 是一樣的，訓練資料就是當看到什麼樣的 state (input)，希望它的 action (output)與人類愈接近愈好。
* Problem 1: Expert only samples limited observation (states)
* Solution 1: Dataset Aggregation (expert 不斷的告訴 actor 要怎麼做，但 actor 這時候還是會自己做自己的事，之後再拿這些資料來訓練 actor）
* Problem 2: If machine has limited capacity, it may choose the wrong behavior to copy.
* Problem 3: In supervised learning, we expect training and testing data have the same distribution.
* Solution: Inverse Reinforcement Learning

### Inverse Reinforcement Learning

* 由 Expert 反推 reward function。
* 先射箭再畫靶：expert 得到的分數一定會比 actor 的分數還要高。
* 只要把 actor 想成 generator，reward function 想成 discriminator，那它就是一個 GAN。
* IRL 訓練過程中不需要太多的訓練資料，通常只有少許的 exper demonstration，實際上機器還是可以跟環境互動非常多次
* ![[Pasted image 20240504180454.png]]
* ![[Pasted image 20240504180627.png]]
* Third Person Imitation Learning
	* 希望利用feature extractor讓機器的第一人稱、第三人稱視野所看到的東西一樣，只抽出重要的資訊。
* Maximum likelihood 對應到 Imitation learning 就是behavior cloning，但光這樣是不足的，應該用 Sequence GAN，而Sequence GAN 對應到的就是 IRL。

