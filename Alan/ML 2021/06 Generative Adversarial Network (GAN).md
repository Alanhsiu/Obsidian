
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
	2. **固定 generator G，更新 discriminator D
	3. **固定 discriminator D，更新 generator G**
	4. 重複步驟 2. 和 3.
	* generator 的參數是隨機初始化的，例如從高斯分布中 random sample 一堆 vector 丟到 generator，起初一些圖片會跟正常的二次元人物非常的不像
	* 對於 discriminator 來說，這就是一個分類或是回歸問題。需要拿真正的二次元人物頭像跟 generator 產生出來的結果，去訓練 discriminator 來分辨他們的差異
* Conditional Generation
	* case 1: Text-to-Image
		* 操控 generator 的輸出，給它 condition x，再從一個簡單分布中抽樣 z，讓 generator 根據 x 和 z 來產生圖片 y​
		* discriminator 不再只輸入圖片 y，它還要輸入 condition x。一方面圖片要好，另外一方面圖片跟文字的敘述必須要相配，discriminator 才會給高分
	* case 2: Image Translation（pix2pix）
		* 單純利用 supervised learning 訓練會造成輸出模糊，因為同樣的輸入可能對應到不一樣的輸出（同一個轉角，小精靈可能左轉也可能右轉，最後學到的就是同時左轉跟右轉）
		* 單純利用 GAN 產生出來的圖片雖比較真實，但是問題是它的想像力過度豐富，出現不該出現的東西
		* **結合 GAN 跟 supervised learning，測試上就可以有比較好的結果**
	* case 3: Sound-to-Image
	* case 4: 產生會動的圖像
* Learning from Unpaired Data
	* 把 GAN 應用在 unsupervised learning 上，因為有時無法蒐集到成對的資料（稱為 unlabeled data）
	* 影像風格轉換
		* 套用原來的方法，但這邊將 sample 的對象從一個 simple distribution 改為 domain x，而 discriminater 利用 domain y 中的圖像做訓練，確保輸出圖片屬於 domain
		* ![[Pasted image 20231001212421.png]]
	* Cycle GAN
		* 有一個循環，從 $x$ 到 $y$ 在從 $y$ 回到 $x$，是一個 cycle 所以叫做 Cycle GAN。利用這種架構，強迫 generator 輸出的 domain $y$ 圖片跟輸入的 domain $x$ 圖片有一些關係
		* 增加第二個 generator，第一個 generator 的工作是把 $x$ 轉成 $y$，第二個 generator 的工作是要把 $y$ 還原回原來的 $x$，而 discriminator 的工作仍然是要看第一個 generator 的輸出像不像是 domain $y$ 的圖
		* ![[Pasted image 20231001212551.png]]
		* Cycle GAN 可以是雙向的，給橘色的 generator domain y 的圖片，讓它產生 domain x 的圖片，然後輸入到藍色的 generator 還原回原來 domain y 的圖片
		* ![[Pasted image 20231001212619.png]]