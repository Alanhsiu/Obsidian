* Image Classification
	1. 把所有圖片都先 rescale 成大小一樣
	2. 把每一個類別表示成一個 one-hot vector
	3. 將圖片輸入到模型中
* 直覺思路會直接展平，但會導致參數量過大 → 像辨識問題本身的特性，其實並不一定需要 fully connected
* Receptive Field
	* 模型通過識別一些特定 patterns 來識別物體，每個神經元只需要考察自己特定範圍內的圖像訊息，將圖像內容展平後輸入到神經元中即可
	* ![[Pasted image 20230912192551.png]]
* Parameter Sharing
	* 對每個 receptive field，都使用一組相同的神經元進行守備；這一組神經元被稱作 Filter，對不同 receptive field 使用的 Filter 參數相同
* Convolutional Layer
	* Pros: 卷積層是“受限”（彈性變小）的 Fully Connected Layer
	* 一般而言，model bias 小、model 的 flexibility 很高的時候，比較容易 overfitting。fully connected layer 可以有各式各樣的變化，但是它可能沒有辦法在任何特定的任務上做好
	* ![[Pasted image 20230912193836.png]]
* Basic Definition
	* 卷積層中有若干個 filters，每個 filter 可以“抓取”圖片中的某一種 pattern
	* filter 的參數就是神經元中的 weight
	* filter 的計算是“內積”
	* 不同的 filter 掃過一張圖片，將會產生“新的圖片”，每個 filter 將會產生圖片中的一個 channel → feature map
	* ![[Pasted image 20230912194549.png]]
	* ![[Pasted image 20230912194817.png]]
* Two views
	* Neuron 角度：只要守備receptive field / 守備不同 receptive field 的神經元可以共用參數
	* Filter 角度：使用 Filter 偵測模式 pattern / Filter 掃過整張圖片
* Subsampling (Pooling)
	* 舉例而言，把偶數行拿掉，把基數列拿掉，不會影響圖片的辨析，同時可以減少運算量
	* eg. Max Pooling, Mean Pooling
	* 