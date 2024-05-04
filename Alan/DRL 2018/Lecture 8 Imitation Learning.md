
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

* 