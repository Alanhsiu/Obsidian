
* 沒幾個遊戲是用 Policy Gradient 可以玩的起來的，Q-learning 相較效果較好，也較穩定。
* Continuous actions，像是自駕車，要決定方向盤左、右轉幾度，或是機器人，每一個 action 對應身上的關節的角度。因此，這類的 action 並不是 discrete，而是vector，vector 內的每一個 dimension 都對應一個 value 都是 real number。
* 在 continuous 情況下卻無法窮舉所有 action 來確認那一個 action 可以讓 Q 最大
* Solutions
	* sample 大 N 個 action 來計算，但這可能不是那麼精確
	* 用 gradient ascent 來解這個問題，將 action 視為 parameter，找一組來 maximize Q-function 並不一定能找到最佳結果，可能是區域最佳解且運算量很大
	* 特別數計一個 network，讓