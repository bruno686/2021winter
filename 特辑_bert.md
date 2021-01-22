#### Transformer

了解bert之前首先要了解transformer。

因为从名字上看，bert就是来自于transformer的组合。**B**idirectional **E**ncoder **R**epresentations from **T**ransformers。

<img src="C:\Users\10119\AppData\Roaming\Typora\typora-user-images\image-20210121091002783.png" alt="image-20210121091002783" style="zoom:50%;" />

在single direction的情况下要想求出b~4~，就要依赖于a^1^ a^2^ a^3^ a^4^，所以输出b^1^ b^2^ b^3^ b^4^，一定是按照顺序来执行的。==因此很难并行产出数据==。

用CNN也可以产生同样的效果，叠很多层的filter也可以产生同样的效果。好处是可以平行计算。坏处是要叠很多层才可以获得整个序列的信息。

可以用self-attention来取代RNN。

bert的结构来自transformer模型的Encoder。Transformer的内部结构由self-attention Layer和Layer normalization的堆叠组合而成。

[<img src="https://s3.ax1x.com/2021/01/20/sW5Zdg.png" alt="sW5Zdg.png" style="zoom: 50%;" />](https://imgchr.com/i/sW5Zdg)

可以在仅一个附加输出层的情况下对经过预训练的BERT模型进行微调，以创建使用与各种任务（问题解答和语言推断）的最新模型，进而减少对NLP任务精心设计特点体系结构的需求。

self-attention later的出现原因：

为了解决RNN，LSTM等常用于处理序列化数据的网络结构无法在GPU中并行加速计算的问题。l