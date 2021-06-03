# Problem Statement

1. Download the StanfordSentimentAnalysis Dataset from this link  (Links to an external site.)(it might be troubling to download it, so force download on chrome). Use "datasetSentences.txt" and "sentiment_labels.txt" files from the zip you just downloaded as your dataset. This dataset contains just over 10,000 pieces of Stanford data from HTML files of Rotten Tomatoes. The sentiments are rated between 1 and 25, where one is the most negative and 25 is the most positive.
2. Train your model and achieve 60%+ validation/text accuracy. Upload your collab file on GitHub with readme that contains details about your assignment/word (minimum 250 words), training logs showing final validation accuracy, and outcomes for 10 example inputs from the test/validation data.
3. Use "Back Translate", "random_swap" and "random_delete" to augment the data you are training on


## Approach

1. Loaded the train, test and validation datasets from pytreebank package into dataframes. Each of it has a sentence and a label [0-4 range] and below are their shapes  
![image](https://user-images.githubusercontent.com/24980224/120672755-3658a780-c4b0-11eb-8a6c-0e02109c6864.png)


