# **Hate speech detection using deep learning**

## :laughing: Overview
The goal of this study is to present a comparative study of deep learning techniques (Simple RNN, LSTM, GRU) for classifying hate speech and offensive language speech from a Twitter dataset. As machine learning algorithms expect the input data to be in a numerical representation. Word embedding techniques will be employed. This project will compare the utility of three embedding methods (GloVe, Word2Vec, Paragram) for hate speech detection by combining them with different deep learning classifiers. This study will compare features and deep learning algorithms to find out which combination of features and algorithm has the best performance.


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
3. The notebook expects `labeled_data.csv` file as the training and validation dataset, and [`glove.6B.100d.txt`](https://www.kaggle.com/datasets/danielwillgeorge/glove6b100dtxt) file to create GLoVe word embeddings, [`word2vec.txt`](https://www.kaggle.com/datasets/wmc1999/imdb-word2vec) file to creat Word2Vec word embeddings, and [`paragram_300_sl999.txt`](https://www.kaggle.com/datasets/ranik40/paragram-300-sl999) file to creat Paragram word embeddings. 
4. The created models should be saved in `models` folder created during the execution.
5. Performance metrics and training metrics plots will be saved in the `images` folder.


## 	:four_leaf_clover: Model Evaluation

Note: As our dataset is unbalanced, we used macro average in our evaluation to give each class equal importance rather than each example.


### **1. Simple RNN**

|       Time | Model Name | Precision |   Recall | F1 Score | Accuracy |
| ---------: | ---------: | --------: | -------: | -------: | -------: |
| 2022-12-11 |Simple RNN|0\.7065974811829236|0\.602714294859484|0\.5969627469269978|0\.8668818071803146|

### **2. LSTM**

|       Time | Model Name | Precision |   Recall | F1 Score | Accuracy |
| ---------: | ---------: | --------: | -------: | -------: | -------: |
|2022-12-11  |LSTM|0\.754609558228147|0\.6482587542410857|0\.6768415997818013|0\.8810004033884631|

### **3. GRU**

|       Time | Model Name | Precision |   Recall | F1 Score | Accuracy |
| ---------: | ---------: | --------: | -------: | -------: | -------: |
|2022-12-11  |GRU         |0\.7531779718608567|0\.6563781661438662|0\.6796358449814024|0\.8805970149253731|


### **4. Weighted GRU**

To handle the unbalanced dataset, we added the class weight by calculating the following formula: `w_j = n_samples / (n_classes * n_samples_j)`

Computed class weights: `{0: 5.776923076923077, 1: 0.43048462741010945, 2: 1.9843862599087196}`

|       Time |    Model Name | Precision |   Recall | F1 Score | Accuracy |
| ---------: | ------------: | --------: | -------: | -------: | -------: |
|2022-12-11  |Weighted GRU   |0\.6666025392298459|0\.8167125450782068|0\.7013733825228265|0\.8087938684953611|




:handshake: I'd like to recognize and appreciate Tushar Samantaray's contribution to this project.
