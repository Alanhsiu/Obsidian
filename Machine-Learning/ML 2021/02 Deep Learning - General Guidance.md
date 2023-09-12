* 訓練資料上的 Loss
	* **Model Bias**: 可以讓 loss 變低的 function 不在 model 可以描述的範圍內→ 重新設計一個更複雜/更有彈性的model
	* Optimization: 深的 model 明明彈性比較大，但 loss 卻沒有辦法比淺的 model 壓得更低，那就代表 optimization 有問題
* 測試資料上的 Loss
	* **Overfitting**: training 的 loss 小，testing 的 loss 大 → 增加訓練集 / 限制模型彈性(如給較少的參數 / early stopping / regularization / dropout)
* Bias-Complexity Trade-off
	* 隨著 model 越來越複雜，training 的 loss 可以越來越低，當 model 越來越複雜的時候，剛開始 testing 的 loss 會跟著下降；但是當複雜的程度超過某一個程度以後，testing 的 loss 就突然暴增
	* ![[Pasted image 20230911121540.png]]
* Cross Validation
	* 把 training 的資料分成兩部分，一部分叫作 training set，一部分是 validation set
	* 在 validation set 上面去衡量它們的分數，根據 validation set 上面的分數去挑選結果，不要管在 public testing set 上的結果以避免 overfitting
	* ![[Pasted image 20230911121926.png]]
* N-fold Cross Validation
	* N-fold Cross Validation 就是先把訓練集切成 N 等份，切完以後拿其中一份當作 Validation Set，另外 N-1 份當 training set，重覆 N 次
	* ![[Pasted image 20230911122153.png]]
* Mismatch
	* 訓練集跟測試集的分佈是不一樣的，依照對數據本身的理解來判斷
	* ![[Pasted image 20230911123239.png]]
	