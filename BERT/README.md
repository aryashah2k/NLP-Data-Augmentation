# BERT

BERT is a language representation model which stands for bidirectional encoder representations from Transformer. This model was open sourced by Google in 2018.

![B1](https://github.com/aryashah2k/NLP-Data-Augmentation/blob/main/BERT/assets/B1.png)

It has a wide range of applications in NLP. It was trained on a large amount of text data from Wikipedia and Book Corpus. Google achieved state of the art accuracy in a variety of NLP tasks using BERT. This model is trained on two tasks masked word prediction and next sentence prediction.

During implementation, we will use BERT to predict masked words and using the predicted words, we will augment our dataset.

Let's consider the same example that we used in data augmentation using word embeddings.

`Any man who must say I'm the king is no true king.` 

Now, the idea is to mask particular key word in the sentence and let BERT predict that key word. In this example, we can mask the last word king.

This new sentence will be given as input to BERT. in the output, BERT returns multiple sentences with possible predictions for the masked words like warrior and prince in data augmentation.

![B2](https://github.com/aryashah2k/NLP-Data-Augmentation/blob/main/BERT/assets/B2.png)

Using word embeddings, we were generating similar words for key words, but not every generated similar word was relevant to the context of our sentence. Like the word throne was also getting generated as similar word for king but it's not relevant for this sentence.

This doesn't happen in the case of BERT. BERT takes the entire sentence as input. This helps the model to understand the context and predict relevant outcomes.

For example, consider the sentence

`Men should wear a shirt and tie for tomorrow's event.` 

If we mask the word tie and ask BERT to predict this word, we get outcomes like tie, pants and jeans. But if we generate similar words for tie using word embeddings, we get words like tied, tying and knotted which are not relevant to what we are looking for here. BERT makes use of both the words which are to the left and the words to the right of the masked word to understand the context and predict the masked word.

![B3](https://github.com/aryashah2k/NLP-Data-Augmentation/blob/main/BERT/assets/B3.png)

Here, if we mask the word shirt, we get outcomes like suit, coat and jacket from BERT Words like pants and genes are not predicted because they are less likely to occur before the word tie. If it masks the word tie and unmask the word shirt, words like suite and coat are not predicted as outcomes for a tie because they are less likely to occur after the words shirt.

This makes BERT extremely useful for our use case.

The quality of augmented data generated using BERT is better than the quality of augmented data using context free word embedding. So our approach will have following simple steps:

1. Mask key words in our dataset.

2. Input the masked sentences to BERT. 

3. As an output, we'll get multiple predictions for the masked words which in turn augments our dataset.

![B4](https://github.com/aryashah2k/NLP-Data-Augmentation/blob/main/BERT/assets/B4.png) 

Since BERT can understand context most of the predicted outcomes will be relevant to the dataset.

-----------------------------------------------

So this approach requires less supervision as compared to the data augmentation using word embeddings. BERT is available in multiple languages, there is also a multilingual version of BERT that can understand 100 plus languages.

Suppose we have a German sentence.

`Berlin has the largest train station in Europe.`

If we mask the word largest and input this sentence to multilingual BERT, we get these predictions, these are relevant to the context of the sentence.

Multilingual BERT automatically outputs German predictions for the masked word. We don't have to mention input is in which particular language. But if a language specific version of BERT is available for your language, that might give you better results than multilingual BERT.

![B5](https://github.com/aryashah2k/NLP-Data-Augmentation/blob/main/BERT/assets/B5.png)

So this approach is extensible to multiple languages but results may not be very accurate as compared to English. It depends on your dataset and the version of BERT you you're using

