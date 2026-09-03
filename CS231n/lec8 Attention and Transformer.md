
#### Origin -- RNN

先理解RNN（Recurrent Neural Network）
RNN用于理解语言（有前后文关系，有逻辑联系）
因此RNN的函数是$$h_t = f(W_xx_t + W_hh_{t-1}+b)$$
ht是对前t个内容的“记忆”，被传入t+1个内容的元素处理里面

##### Encoder
普通RNN -- 只保留最后一次的数据 比如 A B C只保留zui ho