
### Introduction

* 如果今天連 Reward 都沒有，那該如何處理?
* 又稱為 learning by demonstration，或稱 apprenticeship(學徒) learning。
* 現實上難以定義 reward，但是可以收集很多人、專家的範例，那就可以考慮使用 imitation learning。
* 有兩種方法：Behavior Cloning, Inverse Reinforcement learning(inverse optimal control)。

### Behavior Cloning

* 與 supervised learning 是一樣的，訓練資料就是當看到什麼樣的 state (input)，希望它的 action (output)與人類愈接近愈好。
* Problem: Expert only samples limited observation (states)
* Solution: Dataset Aggregation
* 