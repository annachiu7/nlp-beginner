# 任务一：基于机器学习的文本分类
Keywords: machine learning, supervised learning, sentiment classification, numpy, bag-of-word, n-gram, logistic regression, softmax regression, cost function, gradient descent, feature selection, shuffle, batch, mini-batch

## 数据集 Dataset
[Classify the sentiment of sentences from the Rotten Tomatoes dataset](https://www.kaggle.com/c/sentiment-analysis-on-movie-reviews)

This dataset contains test data, train data and a sample submission example.
The test data consists of 156,060 entries and 4 data columns:   
PhraseId  
SentenceId  
Phrase  
Sentiment  

According to kaggle:
> The dataset is comprised of tab-separated files with phrases from the Rotten Tomatoes dataset. The train/test split has been preserved for the purposes of benchmarking, but the sentences have been shuffled from their original order. Each Sentence has been parsed into many phrases by the Stanford parser. Each phrase has a PhraseId. Each sentence has a SentenceId. Phrases that are repeated (such as short/common words) are only included once in the data.

The sentiment labels are:  
> 0 - negative  
> 1 - somewhat negative  
> 2 - neutral  
> 3 - somewhat positive  
> 4 - positive  


## 知识点 Things to Know

### 文本特征表示  Text Feature Representaions

#### Bag-of-word (BOW)
In this model, a text is represented as a bag of its words, where the occurence of each word is used as a feature.

Example:  
text1: I have a mac.  
text2: I have a book.  
text3: I have a mac. I have a book.  

Presentation with the volcabulary: ['I', 'have', 'a', 'mac', 'book']:  
text1: [1, 1, 1, 1, 0]  
text2: [1, 1, 1, 0, 1]  
text3: [2, 2, 2, 1, 1]  

Advantages:  
+ Simple  

Disadvantages:  
- Too many features if the volcab is large
- Disregards grammar and word order

#### N-gram
N-gram can be seen as an improvement to the bag-of-word model, which takes n words next to each other in the text.

Using the above text1: I have a mac.  
2-gram Volcab: ['I have', 'have a', 'a mac']  
Presentation: [1, 1, 1]  

### 训练、验证、测试集
https://easyai.tech/ai-definition/3dataset-and-cross-validation/

1. 对于小规模样本集（几万量级），常用的分配比例是 60% 训练集、20% 验证集、20% 测试集。
2. 对于大规模样本集（百万级以上），只要验证集和测试集的数量足够即可，例如有 100w 条数据，那么留 1w 验证集，1w 测试集即可。1000w 的数据，同样留 1w 验证集和 1w 测试集。
3. 超参数越少，或者超参数很容易调整，那么可以减少验证集的比例，更多的分配给训练集。

### 评估指标 Evaluation
Accuracy: The p of correct predictions among all test data.  
Precision (sensitivity): The p of actual class-i data among all predicted class-i data.  
Recall: The p of correct predictions out of all actual class-i data.  
F1=(2×Precision×Recall)/Precision+Recall）
