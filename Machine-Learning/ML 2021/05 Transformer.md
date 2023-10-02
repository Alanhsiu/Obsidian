
* Seq2Seq Model
	* Transformer 是一個序列到序列（Sequence-to-Sequence，Seq2Seq）的模型。序列到序列模型輸入和輸出都是一個序列，輸入與輸出序列長度之間的關係有兩種情況：一是輸入跟輸出的長度一樣；二是機器自行決定輸出的長度。
* 應用
	* 語音識別：輸入是聲音訊號的一串的 vector，輸出是語音辨識的結果,也就是輸出的這段聲音訊號，所對應的文字 ⇒ 輸出的長度由機器自己決定
	* 機器翻譯：機器讀一個語言的句子，輸出另外一個語言的句子，輸入的文字的長度是 N，輸出的句子的長度是 N'，N 跟 N' 之間的關係也由機器自己來決定
	* 語音翻譯：將聽到的英文的聲音訊號翻譯成中文文字
		* 把語音識別系統跟機器翻譯系統接起來就直接是語音翻譯，為何還需獨立出語音翻譯？
		* 因為世界上很多語言沒有文字，無法做語音識別。因此需要對這些語言做語音翻譯，直接把它翻譯成文字
	* 語音合成：輸入文字、輸出聲音信號就是語音合成（Text-To-Speech，TTS）
		* 現在還沒有真的做端到端（end-to-end）的模型，以閩南語的語音合成為例，其使用的模型還是分成兩階，首先模型會先把中文的文字轉成閩南語的**拼音**，再把閩南語的拼音轉成**聲音信號**
	* 聊天機器人：輸入輸出都是文字，文字是一個向量序列，所以可用序列到序列的模型來做一個聊天機器人
	* QA 任務：很多自然語言處理的任務都可以想成是問答（Question Answering，QA）的任務，如翻譯、自動摘要、情感分析
	* 文法剖析：文法剖析任務中，輸入是一段文字，輸出是一個樹狀的結構，而一個樹狀的結構可以看成一個序列，該序列代表了這個樹的結構
	* 多標籤（Multi-label）分類：
		* Multi-class：從數個 class 裡面選擇某一個 class
		* Multi-label：同一個 sample 可以屬於多個 class
		* 多標簽分類（multi-label classification）問題不能直接把它當作一個多分類問題的問題來解。就算取一個 threshold，只輸出分數最高的前三名，但因 sample 對應的類別的數量可能根本不一樣，因此需要用 Seq2seq 模型，讓機器自己決定輸出類別的數量。
		* ![[Pasted image 20231002153656.png]]
* Transformer 架構
	* 一般的 Seq2Seq 模型會分成 encoder 和 decoder，**encoder 負責處理輸入的序列，再把處理好的結果給 decoder 決定要輸出的序列**
	* Encoder：
		* 編碼器要做的事情就是給一排向量，輸出另外一排向量。
		* 自注意力、循環神經網絡（Recurrent Neural Network，RNN）、卷積神經網路都能做到。
		* ![[Pasted image 20231002154400.png]]
		* Encoder 中會分成很多的 block，每一個 block 都是輸入一排向量，輸出一排向量。最後一個 block 會輸出最終的向量序列
		* Encoder 的每個 block 並不是神經網絡的一層，在每個 block 中，輸入一排向量後做 Self-attention，考慮整個序列的信息，輸出另外一排向量。接下來這排向量會進到 FC，輸出另外一排向量，這一排向量就是一個 block 的輸出
		* ![[Pasted image 20231002154922.png]]
	* Transformer 的 Encoder：
		* 加入了 residual connection 和 layer normalization 的設計
		* 步驟
			1. 考慮全部向量經由 Self-attention 得到輸出向量 a，向量 a 加上其輸入向量 b 得到新的輸出，稱為 residual connection
			2. 計算輸入向量 a+b 的 mean 和 standard deviation，做 layer normalization
			3. 得到的輸出作為 FC 的輸入，FC 輸出結果和原輸入做 residual connection，再做一次 layer normalization 得到的輸出就是 Transformer Encoder 中一個 block 的一個輸出向量
		* N 表示 N 個 block。首先在輸入需要加上 positional encoding。Multi-head attention 就屬 Self-attention。過後再做 residual connection 和 layer normalization，接下來還要經過 FC，接著再做一次 residual connection 和 layer normalization。如此是一個 block 的輸出，總共會重覆 N 次
		* ![[Pasted image 20231002155317.png]]
		* ![[Pasted image 20231002155327.png]]
	* Decoder：
		* autoregressive（AT）：以 encoder 的向量為輸入，並加上特殊的 token 符號 <BOS>（Begin Of Sequence）。在 NLP 中，每一個 token 都可以用一個 one-hot vector 表示，其中一維是 1，剩餘都是 0