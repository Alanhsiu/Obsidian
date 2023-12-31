
* **Self-supervised learning** 
	* self-supervised learning 屬於 unsupervised learning 的一種，其資料本身沒有標籤，但是**訓練過程中實際上有模型自己生成的標籤**
	* 把訓練資料分為兩部分，一部分為輸入資料、另一部分為標註資料
	* ![[Pasted image 20230913100243.png]]
* **BERT**
	* 是一個 **transformer 的 encoder**
	* 輸入一排向量，然後輸出另一排向量，輸出的長度與輸入的長度相同
	* 訓練 BERT 有兩個任務，分別是 Masking Input 及 Next Sentence Prediction
	* **Masking Input**
		* 方法一：用一個特殊的 token “MASK” 蓋住句子中的一個詞
		* 方法二：隨機把某一個字換成另一個字
		* 兩種方法都可以使用，使用哪種方法也是隨機決定的
		* 本質上就是在解決一個分類問題，BERT 要做的是預測什麼字被蓋住
	* **Next Sentence Prediction**
		* 在兩個句子之間添加一個特殊標記 [SEP]，代表兩句子的分隔，如此 BERT 就知道是兩個不同的句子，此外還會在句子的開頭添加另一個特殊標記 [CLS]
		* 只看 [CLS] 的輸出，把它乘以一個 linear transform，做一個二分類問題，輸出 yes/no，判斷兩句是否前後連續
		* 另一種更有用的方法叫做 Sentence Order Prediction，該方法選擇兩個句子本來就是連接在一起，但順序可能顛倒或沒有顛倒兩種可能性，BERT 要回答是哪一種可能性。（ALBERT）
	* BERT 可以用於其他任務，這些任務不一定與填空有關， 它可能是完全不同的東西，這些任務是真正使用 BERT 的任務，其稱為 **downstream tasks**
		* 預訓練（Pre-train）：產生 BERT 的過程
		* 微調（Fine-tune）：利用一些特別的訊息，使 BERT 能夠完成某種任務
		* GLUE 指標（General Language Understanding Evaluation）：測試 self-supervised 學習的能力
		* eg. Sentiment analysis / POS tagging / Natural Language Inference (NLI) / Extraction-based Question Answering (QA)
		* ![[Pasted image 20230913105423.png]]
	* **Embedding**
		* 輸入一串文字，每個文字都有對應的向量
		* 這些向量代表了輸入詞的含義 → 比較相似的詞，它們的向量比較接近


* **應用場景：圖像分類** (by ChatGPT)

假設我們有一個包含各種動物圖像的數據集，並且我們想要訓練一個機器學習模型，該模型能夠將這些圖像分為三個類別：狗、貓和鳥。

1. **監督學習**：
    - 在監督學習中，我們需要一組帶有標籤的訓練數據，即每張圖像都有相應的標籤（狗、貓或鳥）。
    - 我們將這些標籤用於訓練模型，模型學會根據圖像的特徵預測它們屬於哪個類別。
    - 在訓練完成後，我們可以使用這個模型對新的圖像進行分類。
2. **無監督學習**：
    - 在無監督學習中，我們不會提供標籤。相反，我們讓模型自行發現數據的結構。
    - 一個可能的無監督學習應用是聚類分析，其中模型試圖自動將圖像分為不同的群體，而不知道這些群體代表什麼。
    - 在這個情況下，模型可能會將相似的圖像聚集在一起，但不會知道這些聚類代表狗、貓或鳥。
3. **自監督學習**：
    - 在自監督學習中，我們不提供明確的標籤，但我們設計一個自監督任務來生成偽標籤。
    - 例如，我們可以將每張圖像中的某些部分遮蓋起來，然後要求模型預測被遮蓋的部分是什麼。這就創建了一個自監督任務。
    - 模型通過解決這個任務學會了有關圖像的某些特徵，例如，識別狗的尾巴、貓的耳朵等。
    - 這些學到的特徵可以用於後續的分類任務，例如，區分狗、貓和鳥。
    - 允許模型從大量未標記的數據中學習有用的表示。

總之，監督學習使用明確的標籤來訓練模型，無監督學習讓模型自行發現數據結構，而自監督學習通過設計自監督任務來生成偽標籤，幫助模型學習有用的特徵。在不同情境下，這些方法都有其獨特的應用和優勢。