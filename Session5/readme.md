# Sentiment Analysis using LSTM

## Problem Statement

1. Download the StanfordSentimentAnalysis Dataset from this link  (Links to an external site.)(it might be troubling to download it, so force download on chrome). Use "datasetSentences.txt" and "sentiment_labels.txt" files from the zip you just downloaded as your dataset. This dataset contains just over 10,000 pieces of Stanford data from HTML files of Rotten Tomatoes. The sentiments are rated between 1 and 25, where one is the most negative and 25 is the most positive.
2. Train your model and achieve 60%+ validation/text accuracy. Upload your collab file on GitHub with readme that contains details about your assignment/word (minimum 250 words), training logs showing final validation accuracy, and outcomes for 10 example inputs from the test/validation data.
3. Use "Back Translate", "random_swap" and "random_delete" to augment the data you are training on


## Solution

1. Loaded the train, test and validation datasets from pytreebank package into dataframes. Each of it has a sentence and a label [0-4 range] and below are their shapes  
![image](https://user-images.githubusercontent.com/24980224/120672755-3658a780-c4b0-11eb-8a6c-0e02109c6864.png)

2. Augmentation techniques Translate, Random Swap and Random Delete are applied on the dataset. 
    Translate : Randomly selected sentences from the train dataset are translated to a different language and they are retranslated back to english sentences
    Random Delete: Random words are deleted from a random set of sentences
    Random Swap: Randomly selected words in a sentence are swapped and this is performed n times in each sentence and this is performed for a random set of sentences

3. Sentences are tokenized using spacy and are converted to lower case 
4. The dataset has been converted to iterators using BucketIterator with a batch size of 32
5. Below is the proposed network for training the sentiment model
![image](https://user-images.githubusercontent.com/24980224/121193493-84dcbc00-c88b-11eb-95da-c72fa6393988.png)

6. In the embedding layer, we have used pre trained glove 100d vectors and the weight matrix for the embedding layers are not updated
7. Post the embedding layer, the embedding vectors are passed to LSTM layer and 2 fully connected Linear layers
8. Adam optimizer has been used and Cross entropy loss is used as the loss function
9. The network has been trained for 200 epochs below are the training logs
![image](https://user-images.githubusercontent.com/24980224/121194543-7511a780-c88c-11eb-9ab4-be44f440cfe0.png)

10. Below is training  loss and validation loss

Training Loss
![image](https://user-images.githubusercontent.com/24980224/121194646-8fe41c00-c88c-11eb-996e-830bb41321d6.png)

Validation Loss
![image](https://user-images.githubusercontent.com/24980224/121194728-a12d2880-c88c-11eb-9a40-ad5a5aef1f94.png)

11. When tested on test dataset below are the accuracy and loss values that the model has generated


12. Below is the predictions made by the model on some of the test records
 
