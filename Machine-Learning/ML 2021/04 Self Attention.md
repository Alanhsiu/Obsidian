* 輸入是向量序列
	* 文字處理
		* one-hot encoding: 一個很長的向量，長度跟世界上存在的詞彙的數量一樣多
		* word embedding: 給每一個詞彙一個向量，這個向量是包含語義訊息的，而一個句子就是一組長度不一的向量
	* 聲音信號處理
		* 會把一段聲音訊號取一個範圍，這個範圍叫做一個窗口（window），把該窗口裡面的訊息描述成一個向量，這個向量稱為一幀（frame）
	* 圖
		* eg. social network, molecule
* 輸出有三種可能性
	1. 每一個向量都有一個對應的標簽 → 詞性標註（POS tagging）：機器會自動決定每一個詞彙的詞性，判斷該詞是名詞還是動詞還是形容詞等等
	2. 一組向量序列輸出一個標簽 → 文本情感分析：給機器看一段話，模型要決定這段話是積極的（positive）還是消極的（negative）
	3. 模型自行決定輸出多少個標籤 → 輸入是 N 個向量，輸出可能是 N′ 個標簽，而N′ 是機器自己決定的。此種任務被稱作序列到序列（**Sequence to Sequence**，Seq2Seq），如翻譯、語音辨識
* Self Attention Model
	* 考慮整個序列的所有向量，綜合向量序列整體和單個向量個體，得到對每一個向量處理後的向量，將這些向量個別連接一個 FC，FC 可以專注於處理這一個位置的向量，得到對應結果
	* 輸入：$a^1$ to $a^4$ , can be either input or a hidden layer
	* 輸出：$b^1$ to $b^4$ , 每一個 b 都是考慮了所有的 a 以後才生成出來的
	* 步驟
		1. 根據 $a^1$ 這個向量找出跟其他向量的相關程度 $\alpha$ ![[Pasted image 20230913003205.png]]
		2. 藉由一個計算 attention 的模組來得到 $α$。（q = query、k = key）![[Pasted image 20230913003411.png]]
		3. 計算完 $a^1$ 跟其他向量的相關性 $α$ 後（也必須計算 $a^1$ 跟自己的 $α$），把所有的 $α$ 經過 softmax （也可使用其他激勵函數，如： ReLu）得到 $α'$ ![[Pasted image 20230913004258.png]]
		4. 把向量 $a^1$ 到 $a^4$ 乘上 $W^v$ 得到新的向量：$v^1$、$v^2$、$v^3$ 和 $v^4$，接下來把每一個向量都去乘上 $α'$ 後再求和得到 $b^1$ →如果 a^1 跟 a^2 有高相關性，即 $α'_{1,2}$ 的值很大，再做加權和後，得到的 b^1 就可能會比較接近 v^2。所以誰的注意力的分數最大，誰的 v 就會主導（dominant） 抽出來的結果![[Pasted image 20230913004611.png]]
* Self-Attention vs RNN
	* 同：Recurrent Neural Network 跟 Self-attention 做的事情非常像，它們的 input 都是一個 vector sequence，前一個時間點的輸出也會作為輸入丟進 RNN 產生新的向量，也同時會輸入到 FC
	* 異
		* 對 RNN 來說，假設最右邊黃色的 vector 要考慮最左邊的輸入，那它必須要把最左邊的輸入**存在 memory 中都不能夠忘掉**一路帶到最右邊，才能夠在最後的時間點被考慮 → 無法平行化
		- 對 Self-attention 來說沒有這個問題，它可以在整個 sequence 上非常遠的 vector之間**輕易地抽取訊息** → vector 是平行產生的
		- ![[Pasted image 20230913005756.png]]
* 圖神經網路（GNN）
	* 圖中的 edge 意味著節點之間的關係，所以我們就可只計算有 edge 相連的 node 的 attention，若兩個 node 之間沒有 edge，代表兩個 node 沒有關係，就不必計算 attention
	* ![[Pasted image 20230913010003.png]]
