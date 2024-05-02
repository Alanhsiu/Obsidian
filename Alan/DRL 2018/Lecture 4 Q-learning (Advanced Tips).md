### Double DQN

* DQN: Q value is usually over-estimated (因為總是選擇被高估那個)
* Double DQN: two function Q and Q' (只要其中一個沒有高估某個 action，就不會選擇錯)
* 實務上原本就有兩個 Q network (Q-function and target network)

### Dueling DQN

* 只改了 network 的架構，演算法不變。
* ![[Pasted image 20240502093847.png]]
### Prioritized Experience Replay

* 原本訓練的過程中，我們會從 buffer 中 uniform 的 sample 資料出來，但這麼不見得是好的，或許有某一筆資料的 TD erro 特別大 (target network 的 output 與 Q-function 的 output 差距)，這意味著過程中的對這筆資料的訓練是沒訓練好的，那就需要給它比較大的機率被sample。 

### Multi-step

* 在 TD 的記錄中，只保存{$s_t, a_t, r_t, s_{t+1}$}，現在調整成保存大N筆資料，以這樣的記錄方式來結合 MC、TD。
* 因為加入更多的 step，因此有了 MC 的缺點，就是 variance 較大，但這部份可以透過調整 N 來控制，在 variance 與 bias 中取一個平衡。

### Noisy Net

* 之前提過的 Epsilon Greedy 是在 action 的 space 上加 noise，但另一種更好的作法，Noisy Net，它是在參數的 space 上加入 noise。
* 在每一個 episode 開始的時候，也就是跟環境互動之前，將 Q-function(nn) 上的參數通通加上一個 Gaussian noise。要注意的是，每次加入 noise 之後的參數就是固定不變，一直到整個結束到下一個episode開始之前才又重新 sample 一次 noise。
* Noise on Action → No real policy works in this way
* Noise on Parameter → Explore in a **consistent** way

### Distributional Q-function

* Q-function 計算出來的是一個 accumulated reward 的期望值(expect)，也就是在某一個 state 採取某一個 action，將玩到遊戲結束的所有 reward 進行一個統計，這邊得到的其實是一個 distribution，然後我們對這個 distribution 計算它的 mean，就是 Q-value。
* 如果用一個 expect Q-value 來代表整個 reward 的話，可能無法 model reward 的 distribution。(不同的 distribution 是可能擁有相同的 mean 的)
* Distributional Q-function 要做的就是 output distribution。
* ![[Pasted image 20240502104542.png]]
### Rainbow

* 把剛才的所有技巧加起來就是 Rainbow，橫軸為 training process，縱軸是玩 "Atari" 的平均分數的和，取的是 median。