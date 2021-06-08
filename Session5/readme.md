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
![image](https://user-images.githubusercontent.com/24980224/121204128-4ac3e800-c894-11eb-8c81-7416d2f066a6.png)


10. Below is training  loss and validation loss

Training Loss

![image](https://user-images.githubusercontent.com/24980224/121204259-64fdc600-c894-11eb-9cae-46cb3b7354f3.png)

Validation Loss

![image](https://user-images.githubusercontent.com/24980224/121204284-6af3a700-c894-11eb-8537-1a9fd919524a.png)

Training Accuracy

![image](https://user-images.githubusercontent.com/24980224/121204364-78109600-c894-11eb-98a3-721704e58810.png)


Validation Accuracy

![image](https://user-images.githubusercontent.com/24980224/121204414-7f37a400-c894-11eb-8762-ca97685ecc35.png)

11. When tested on test dataset below are the accuracy and loss values that the model has generated

![image](https://user-images.githubusercontent.com/24980224/121206990-895aa200-c896-11eb-9f6c-66bf578f764a.png)


12. Below is the predictions made by the model on some of the test records
 
sentence	labels	prediction
a masterful film from a master filmmaker , unique in its deceptive grimness , compelling in its fatalist worldview .	4	3
light , cute and forgettable .	2	0
if there 's a way to effectively teach kids about the dangers of drugs , i think it 's in projects like the ( unfortunately r-rated ) paid .	3	0
while it would be easy to give crush the new title of two weddings and a funeral , it 's a far more thoughtful film than any slice of hugh grant whimsy .	3	2
though everything might be literate and smart , it never took off and always seemed static .	1	1
cantet perfectly captures the hotel lobbies , two-lane highways , and roadside cafes that permeate vincent 's days	3	3
ms. fulford-wierzbicki is almost spooky in her sulky , calculating lolita turn .	3	1
though it is by no means his best work , laissez-passer is a distinguished and distinctive effort by a bona-fide master , a fascinating film replete with rewards to be had by all willing to make the effort to reap them .	3	3
like most bond outings in recent years , some of the stunts are so outlandish that they border on being cartoonlike .	1	1
a heavy reliance on cgi technology is beginning to creep into the series .	2	1
![image](https://user-images.githubusercontent.com/24980224/121213762-2835cd00-c89c-11eb-9745-68191ccf4e3b.png)
