
#### Origin -- RNN

先理解RNN（Recurrent Neural Network）
RNN用于理解语言（有前后文关系，有逻辑联系）
因此RNN的函数是$$h_t = f(W_xx_t + W_hh_{t-1}+b)$$
ht是对前t个内容的“记忆”，被传入t+1个内容的元素处理里面

##### Encoder
普通RNN -- 只保留最后一次的数据 比如 A B C只保留最后一次的处理数据 -- 这个就称为Encoder

最后一次的保留数据：Context Vector/ Encoder Representation

##### Decoder
也是一层RNN，但是是根据前面Encoder的生成内容来**逐步生成Token**
每一步的生成根据这一步的内容以及前面生成的Token $$s_t = f(s_{t-1}, y_{t-1})$$
每次依然是SoftMax的概率分布，然后选择概率最大的Token作为最新的输出

---
#### Attention
因为Encoder-Decoder的结构原因，每次只能看到前一个元素并且存在一个Vector中，会产生记忆不足丢失信息。

