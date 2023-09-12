* Image Classification
	1. 把所有圖片都先 rescale 成大小一樣
	2. 把每一個類別表示成一個 one-hot vector
	3. 將圖片輸入到模型中
* 直覺思路會直接展平，但會導致參數量過大 → 像辨識問題本身的特性，其實並不一定需要 fully connected
* Receptive Field
	* 模型通過識別一些特定 patterns 來識別物體，每個神經元只需要考察自己特定範圍內的圖像訊息，將圖像內容展平後輸入到神經元中即可