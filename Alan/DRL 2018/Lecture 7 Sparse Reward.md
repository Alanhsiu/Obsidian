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

* 你為機器學習做規劃，給它的訓練資料是有順序的。並非 RL 獨有的概念，在很多機器學習都可以用的到。
* 先教簡單的再教難的。例如：訓練 RNN 的時候，由短的 sequence 到長的 sequence。
* Reverse Curriculum Generation：比較通用幫機器設計課程的方法。由目標去反推。
	* 根據 goal state 來找尋其它接近 goal state 的 state。
	* 利用 reward 將極端的 case 去掉。reward 過大代表太簡單，代表機器已經會了。過小代表太難，代表機器現在學不會。
	* 利用對機器比較剛好的 case 再 sample 更多的 state
	* ![[Pasted image 20240504164903.png]]

### Hierarchical Reinforcement Learning

* 有很多個 agent，有的負責 high-level，負責訂目標，再分配給其它 agent 來執行。
* 上層的 output 就是下層的 input，下層再決定自己的 output。
* 如果下層的 agent 無法達成上層所提出的 goal 的話，上層的 agen t就會被討厭而得到一個 penalty。