### Double DQN

* DQN: Q value is usually over-estimated (因為總是選擇被高估那個)
* Double DQN: two function Q and Q' (只要其中一個沒有高估某個 action，就不會選擇錯)
* 實務上原本就有兩個 Q network (Q-function and target network)

### Dueling DQN

* 