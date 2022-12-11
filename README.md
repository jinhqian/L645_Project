# **Hate speech detection using deep learning**

## :laughing: Overview
The goal of this study is to present a comparative study of deep learning techniques (Simple RNN, LSTM, and GRU) for classifying hate speech and offensive language speech from a Twitter dataset. As machine learning algorithms expect the input data to be in a numerical representation. Word embedding techniques will be employed. This project will compare the utility of three embedding methods (GloVe, Word2Vec, and Paragram) for hate speech detection by combining them with different deep learning classifiers. This study will compare features and deep learning algorithms to find out which combination of features and algorithm has the best performance.


## :open_file_folder: Dataset

We used Davidson et al. (2017) Twitter dataset in our experiment.
| Class               | Tweets Count  | Percentage |
| :---                |    :---:      |       ---: |
| Hate Speech         | 1,430         | 5.77%      |
| Offensive Language  | 19,190        | 77.43%     |
| Neither             | 4,163         | 16.80%     |
| Total               | 24,783        |            |

**Data Unbalance:** According to the table, we can find that this dataset contains only 5.77% of Hate Speech. 

## :computer: Tools used 
1. Data Preprocessing - Keras, NLTK
2. Modelling and training - Keras, TensorFlow, Scikit-Learn, 
3. Visualization – Matplotlib, Seaborn,
4. Environment – Google Colab

## :sparkles: Steps to run the code

1. Install the required packages using the following command - `pip install requirements.txt`.
2. Open the `Hate Speech Detection using deep learning` colab notebook and run.
3. The notebook expects `labeled_data.csv` file as the training and validation dataset, and [`glove.6B.100d.txt`](https://www.kaggle.com/datasets/danielwillgeorge/glove6b100dtxt) file to create GLoVe word embeddings, [`word2vec.txt`](https://www.kaggle.com/datasets/wmc1999/imdb-word2vec) file to creat Word2Vec word embeddings, and [`paragram_300_sl999.txt`](https://www.kaggle.com/datasets/ranik40/paragram-300-sl999) file to creat Paragram word embeddings. (Note: 1. When using one of the embedding methods, please comment out the remaining two embedding sections. 2. As paragram embedding needs 300 dimensions, please change the dimensions to 300 from 100 when building models.)

4. We splited files into three folders (`glove`, `word2vec`, and `parargam`) according to the embedding methods. The created deepe learning models should be saved in `_model` folder created during the execution.
5. Performance metrics and training metrics plots will be saved in the `images` folder.


## 	:four_leaf_clover: Model Evaluation

**Note:**
1. As our dataset is unbalanced, we used macro average in our evaluation to give each class equal importance rather than each example.
2. To handle the unbalanced dataset, we also added the class weight by calculating the following formula: `w_j = n_samples / (n_classes * n_samples_j)`.
   Computed class weights are `{0: 5.776923076923077, 1: 0.43048462741010945, 2: 1.9843862599087196}`








### **1. GloVe**

|Time	      |Model Name	   |Precision	|Recall	  |F1 Score	|Accuracy  |
| ---------:| -----------: | --------:| -------:| -------:| -------: |
|2022-12-11	|Simple RNN	   |0.674852	|0.629022	|0.592651	|0.855587  |
|2022-12-11	|LSTM	         |***0.761822***	|0.710427	|***0.725808***	|***0.888665***  |
|2022-12-11	|GRU	         |0.732895	|0.632981	|0.647664	|0.879387  |
|2022-12-11	|Weighted GRU	 |0.658741	|***0.827845***	|0.681948	|0.773296  |
|2022-12-11	|Weighted LSTM |0.668716	|0.809083	|0.711077	|0.826543  |

When we use GloVe as word embedding method, we found that LSTM gave us the highest F1 score. However, as the confusion metrix shown, Weighted GRU 
is good at detecting Hate speech (138 out of 164) and GRU has best performance in detecting offensive language (1824 out of 1905). 

### **2. Word2Vec**


|       Time | Model Name | Precision |   Recall | F1 Score | Accuracy |
| ---------: | ---------: | --------: | -------: | -------: | -------: |
|2022-12-11	|Simple RNN	  |***0.828174***	  |0.401311	|0.406545	|0.791448
|2022-12-11	|LSTM	        |0.672411	  |0.530486	|0.549671	|0.834611
|2022-12-11	|GRU	        |0.68977	  |0.52939	|0.554318	|***0.836628***
|2022-12-11	|Weighted GRU |0.555315	  |0.662641	|0.557043	|0.676079
|2022-12-11	|Weighted LSTM|0.563203	  |***0.6656***	|***0.557435***	|0.670835

As the result shows, we can find that Word2Vec performs worse than GloVe when it combined with Simple RNN, LSTM, and GRU. When we use Word2Vec as word embedding method, Weighted LSTM gave us the highest F1 score. Confusion metrix shows that Weighted LSTM detects the most number of hate speech correctly (100 out of 164), and Simple RNN can detect the most numbers of offensive language correctly (1873 out of 1905).


### **3. Paragram**

|       Time | Model Name | Precision |   Recall | F1 Score | Accuracy |
| ---------: | ---------: | --------: | -------: | -------: | -------: |
|2022-12-11	 |Simple RNN  |0.697894	  |0.654591	|0.635024	|0.870109
|2022-12-11	 |LSTM	     |0.725818	  |0.682147	|0.698595	|0.877370
|2022-12-11	 |GRU         |***0.731907***	  |0.662527	|0.682137	|***0.878983***
|2022-12-11	 |Weighted GRU|0.681125	  |***0.800923***	|***0.716065***	|0.835418
|2022-12-11	 |Weighted LSTM|0.671039  |0.785301	|0.706374	|0.832190

We also tried Paragram word embedding. As the result shown, Weighted GRU gave us the highest F1 score. According to the confusion metrix, we found that Weighted GRU detects hate speech best (109 out of 164), and GRU detects the most number of offensive language correctly (1807 out of 1905). 

## :smiling_face_with_three_hearts: Conclusion

In this project, we attempted to combine different word embedding methods with deep learning techniques to find out which combination gives us the best performance.  According to the comparison, we concluded that GloVe + LSTM gave us the highest F1 score. In terms of best performance in detecting hate speech and offensive language, we found that  GloVe + Weighted GRU detects the most hate speech corretly in tweets, and Word2Vec + Simple RNN detects the most offensive language corretly in tweets. Therefore, we could change and deciede which combination to use depending on the goal of our study.

Thank you!

:handshake: I'd like to recognize and appreciate Tushar Samantaray's contribution to this project.
