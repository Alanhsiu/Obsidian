* Critical Point
	* 所有 eigen value 都是正的，H 是 positive definite（正定矩陣），此時是 local minima
	* 所有 eigen value 都是負的，H 是 negative definite，此時是 local maxima
	* 如果 eigen value 有正有負，代表是 saddle point
	* Loss 在一個維度很高的空間中，往往只會遇到鞍點而幾乎不會遇到局部極小值點
* Batch 
	* 在 update 參數的時候，我們是拿 B 個樣本出來，算 loss、算 gradient
	* 所有的 batch 看過一遍，叫做一個 epoch
	* 因為有平行運算的能力，因此實際上當 batch size 小（batch 數量多）的時候，要跑完一個 Epoch 花的時間比大的 batch size 還要多；反之，大的 batch size 下，跑完一個 Epoch 花的時間反而是比較少的
	* 使用較小的 Batch Size，在更新參數時會**有 Noisy** → 有利於訓練
	* 使用較小的 Batch Size 可以**避免 Overfitting** → 有利於測試
* Momentum
	* Vanilla Gradient Descent (一般的梯度下降): 只考慮梯度的方向，往反方向移動
	* Gradient Descent + Momentum (考慮動量): update 的方向不是只考慮現在的 gradient，而是考慮過去所有 gradient 的總合
	*  **較小的 batch size 和 momentum 可幫助離開 critical points**
* Adaptive Learning Rate
	* Adagrad: 考慮之前所有的梯度大小 → 不能實時考慮梯度的變化情況
	* RMSProp: 添加參數 \alpha，越大說明過去的梯度訊息更重要
	* Adam: RMSProp + Momentum
* Learning Rate Scheduling
	* Learning Rate Decay: 隨著時間的不斷地前進，η^t 越來越小
	* Warm Up: 讓 learning rate 先變大後再變小
* Batch Normalization
	* 不同的參數發生變化，引起損失函數變化的程度不同，是因受**不同維度輸入值的差異的影響**
	* Feature Normalization（歸一化）
		* 對不同 feature 向量的同一維度進行標準化（Standardization）
		* 每一層都需要一次 Normalization