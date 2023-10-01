
* Basic Idea
	* Generator（生成器）：目標是生成與真實數據相似的合成數據。
	* Discriminator（判別器）：目標是區分真實數據和生成器生成的合成數據。
* Network as Generator
	* 輸入 neural network 的除 x 以外，還有一個從某一簡單的（已知）分布中隨機採樣得到的一個 random 的 variable
	* 同樣的input，可能有不同的輸出
	* 目的是希望模型的輸出是 creative，如繪畫、聊天機器人等等
	* ![[Pasted image 20231001193607.png]]
* Unconditional Generator
	* 不考慮 x，只先單純考慮從 simple distribution 採樣出來的 z​
	* z 是從一個 normal distribution 裡 sample 出來的向量，通常會是一個 low-dimensional 的向量，而一張圖片就是一個非常高維的向量，所以 generator 實際上做的事情就是產生一個非常高維的向量，當輸入的向量不同（不同的 z），輸出就會跟著改變
	* ![[Pasted image 20231001194107.png]]
* Discriminator
	* 也是一個 neural network，其中裡面的架構可以自己設計，例如可以使用 CNN、Transformer 等等
	* 把 generator 的輸出（一個高維向量）輸入到 discriminator，discriminator 會產生一個數字 scalar，越大代表 generator 的輸出越真實越合理
* Algorithm
	1. 初始化 generator 與 discriminator
	2. 固定 generator G，更新 discriminator D
	3. 固定 discriminator D，更新 generator G
	4. 重複步驟 2. 和 3.
	* generator 的參數是隨機初始化的，例如從高斯分布中 random sample 一堆 vector 丟到 generator，起初一些圖片會跟正常的二次元人物非常的不像
	* 對於 discriminator 來說，這就是一個分類或是回歸問題。需要拿真正的二次元人物頭像跟 generator 產生出來的結果，去訓練 discriminator 來分辨他們的差異
* Conditional Generation
	* case 1: Text-to-Image
	* 