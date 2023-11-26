* Classification as Regression: class 之間確實有相關性(eg. 1, 2, 3)
* Class as one-hot vector: 寫成向量形式，任兩個 class 的距離都相同
	* Classification with soft-max: normalize 到 0 到 1 之間
	* Loss of Classification: 選擇 cross-entropy，因為比 MSE 更加適用於分類問題
	* ![[Pasted image 20230912120928.png]]
