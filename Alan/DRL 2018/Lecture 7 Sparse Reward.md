### Reward Shaping

* 環境中有一個固定的 reward，它是真正的 reward，但我們為了要讓機器可以學習，因此設置一些 reward 來引導 agent。
* Curiosity
	* 在原始 reward function 之外再加入一個額外的 reward function (ICM, intrinsic curiosity module)
	* 根據機器預測的 $s_{t+1}$ 與真實的 $s_{t+1}$ 像不像，越不像 reward就愈大，鼓勵模型冒險。
	* 問題：有一些 state 不好預測，但它也不見得是好的，也許這些 state 是不應該被嘗試的。
	* 結論：所以有好奇心是不夠的，還要讓機器知道什麼樣的事情是真正重要的。
	* 解決方法：加入 feature extractor，因為要用抽出的 feature 預測 action，因此如果本質上是跟 action 無關的資訊就會被濾掉，自然不會出現在 feature representation。
	* ![[Pasted image 20240504164051.png]]
	* ![[Pasted image 20240504164413.png]]
### Curriculum Learning

* 