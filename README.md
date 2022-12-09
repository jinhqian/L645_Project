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

## :sparkles: Steps to run the code

1. Install the required packages using the following command - `pip install requirements.txt`.
2. Open the `Hate Speech Detection using deep learning` colab notebook and run.
3. The notebook expects `labeled_data.csv` file as the training and validation dataset, and `glove.6B.100d.txt` file to create GLoVe word embeddings, `word2vec.txt` file to creat Word2Vec word embeddings, and `paragram_300_sl999.txt` file to creat Paragram word embeddings. All of them are available inside `data` folder.

+ The created models should be saved in `models` folder created during the execution.
- Performance metrics and training metrics plots will be saved in the `images` folder.


## 	:four_leaf_clover: Model Evaluation
### **1. Simple RNN**

|       Time | Model Name | Precision |   Recall | F1 Score | Accuracy |
| ---------: | ---------: | --------: | -------: | -------: | -------: |
| 2022-04-29 | Simple RNN |  0.579802 | 0.612921 | 0.557847 | 0.845502 |

### **2. LSTM**

|       Time | Model Name | Precision |   Recall | F1 Score | Accuracy |
| ---------: | ---------: | --------: | -------: | -------: | -------: |
| 2022-04-29 |       LSTM |  0.746508 | 0.615625 |  0.62655 | 0.878177 |

### **3. GRU**

|       Time | Model Name | Precision |   Recall | F1 Score | Accuracy |
| ---------: | ---------: | --------: | -------: | -------: | -------: |
| 2022-04-29 |        GRU |  0.742956 | 0.657711 | 0.659135 | 0.887858 |


### **4. Weighted LSTM**

### Calculate class weights

The class weight is calculated using the following formula: `w_j = n_samples / (n_classes * n_samples_j)`

Computed class weights: `{0: 5.776923076923077, 1: 0.43048462741010945, 2: 1.9843862599087196}`


|       Time |    Model Name | Precision |   Recall | F1 Score | Accuracy |
| ---------: | ------------: | --------: | -------: | -------: | -------: |
| 2022-04-29 | Weighted LSTM |  0.670579 | 0.815035 | 0.701791 | 0.809601 |


