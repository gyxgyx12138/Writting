# python日记

#### isinstance()函数
isinstance(object, classinfo)是python的内置函数，用来**检查一个对象是否属于指定的类型**。相比而言，比type()更灵活。


``` python
data = [1,2,3]
print(isinstance(data,(str,tuple,list)))
# 只要data属于(str,tuple,list)中的任何一种类型，都会返回True。
```
输出：
``` plaintext
True
```


#### dict.items()
dict.items()返回一个元组，**解码**这个元组，第一个是键，第二是值。

#### zip()函数
zip()函数的作用是将多个**可迭代对象**（列表、元组）等中对应位置的元素**配对**（按照顺序）成元组，返回一个由这些元组组成的**迭代器**。

``` python
user_ids = ['u1', 'u2', 'u3']
user_embeddings = [1, 2, 3]
zipped = dict(zip(user_ids, user_embeddings))
print(zipped)
```
输出：
``` plaintext
{'u1': 1, 'u2': 2, 'u3': 3}
```
####  使用GPU加速训练过程要注意的点

因为 PyTorch 的张量默认是在 CPU 上的，模型参数默认也是在 CPU 上。如果要利用 GPU 加速，需要**显式**地将模型和数据都转移到 GPU。
``` python
# 检测GPU 是否可用
device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
# 将模型和数据都转移到 GPU
model = model.to(device)
data = data.to(device)

```
#### sentence-bert和一般的bert模型有什么区别？
BERT模型，使用[CLS]或者平均池化作为句子向量。在语义相似度任务表现一般。
sentence-BERT模型专门设计池化策略，并生成固定且有语义意义的句子向量。语义相似度任务表现优异。

#### model.eval()表示什么意思？
model.eval()是切换模型到推理/测试状态，**关闭训练时的随机性和动态统计**，确保模型输出稳定可靠。

#### 如何理解tokenizer，在中文里如何翻译，如何使用tokeinizer处理文本。
- tokenizer在中文里可以翻译为“分词器”，功能将文本划分为最小的单元，如一个单词，一个中国汉字，一个标点符号。每一个最小的单元就叫做token。
- 如果调用bert的tokenizer，那么“Hello,world！”就会被切分为“Hello”,“,”,“world”,“！”。
- 如果调用中文分词器，那么“你好，世界！”就会被切分为“你好”,”，”,”世界”,”！”。