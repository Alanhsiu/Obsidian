### Double DQN

* DQN: Q value is usually over-estimated (因為總是選擇被高估那個)
* Double DQN: two function Q and Q' (只要其中一個沒有高估某個 action，就不會選擇錯)
* 實務上原本就有兩個 Q network (Q-function and target network)

### Dueling DQN

* 只改了 network 的架構，演算法不變。
* ![[Pasted image 20240502093847.png]]
### Prioritized Experience Replay

* 原本訓練的過程中，我們會從 buffer 中 uniform 的 sample 資料出來，但這麼不見得是好的，或許有某一筆資料的 TD erro 特別大 (target network 的 outpu t與 Q-function 的 output 差距)，這意味著過程中的對這筆資料的訓練是沒訓練好的，那就需要給它比較大的機率被sample。 

### Multi-step

* 在 TD 的記錄中，只保存{$st,a$}，現在調整成保存大N筆資料，以這樣的記錄方式來結合 MC、TD。