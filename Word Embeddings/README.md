# Word Embeddings

Using word embeddings we can represent words as vectors in high dimensional space in a meaningful way. Let's say our data consist of following two sentences.

`Winter is coming.`

`Any man who must say I'm the king is no true king.`

![WE1](https://github.com/aryashah2k/NLP-Data-Augmentation/blob/main/Word%20Embeddings/assets/WE1.png)
------------------------------------------------
Now we want to generate more sentences similar to these to augment our dataset or to expand our dataset. Let's focus on the keywords in this sentence(keywords are the words that matter the most and give meaning to the sentence.)

We have three keywords. Winter, man and King, using word embeddings these keywords can be represented as vectors in embedding space. 

![WE2](https://github.com/aryashah2k/NLP-Data-Augmentation/blob/main/Word%20Embeddings/assets/WE2.png)

We can easily augment this data if we can find similar words for these keywords.

![WE3](https://github.com/aryashah2k/NLP-Data-Augmentation/blob/main/Word%20Embeddings/assets/WE3.png)

Suppose we find out following similar words - summer and spring for winter. Woman and boy for man and queen and prince for the King. We can simply replace our key words with these new words and create new sentences to expand our dataset. So our problem reduces down to finding out similar words for our keywords.

This can be easily done using word embeddings. Word embeddings are not just any random vectors. These vectors represent words in such a way that those words which are related to each other are more likely to occur closer in embedding space.

![WE4](https://github.com/aryashah2k/NLP-Data-Augmentation/blob/main/Word%20Embeddings/assets/WE4.png)

Since these words are similar in meaning, they will be closer to each other in a embedding space. If we search in the space surrounding to our key words, we will be able to find out similar words to our keywords.

During Implementation, We will make use of Google News vectors trained using the word to vector model. It has pre-trained word vectors for three million words. so our problem can be solved using the following approach.

1. Find out keywords in our dataset, we cannot apply this technique simply to all the key words in our data that will not help to generate good quality data.

2. Find out similar words using Google News vectors.

3. Replace the key words. Using these new words to generate more data.

![WE5](https://github.com/aryashah2k/NLP-Data-Augmentation/blob/main/Word%20Embeddings/assets/WE5.png)

-----------------------------------------------

There are multiple other popular pre-trained word embeddings like fast text, stanford glove.

You can make use of multiple such pre-trained word embeddings to find a greater number of similar words and generate more data. There are pre-trained word vectors for languages other than English also. So this approach applies to other languages as well, but not every similar word that we get using word embeddings will be relevant to our context.

For example, in the case of this sentence, any man who must say I am the king is no true king, it has the keyword king. for this word, we can get the word throne in its list of similar words because this is very much related to the king.

![WE6](https://github.com/aryashah2k/NLP-Data-Augmentation/blob/main/Word%20Embeddings/assets/WE6.png)

But we can't use this word to replace King in this sentence because it's not relevant to the context of the sentence.

So this approach requires careful supervision also to short list, only the relevant results from the generated outcomes.