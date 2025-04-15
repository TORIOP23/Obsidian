- native Bayes model
- Imagine that for each category (business, weather, etc.) we have a bag full of words, the more common the word, the more slips it is duplicated on)
- Thường sử dụng với **n-grams**
## N-gram word
- The **bag-of-words** model has limitations. For example, the word “quarter” is common in both the business and sports categories. But the four-word sequence “first quarter earnings report” is common only in business and “fourth quarter touchdown passes” is common only in sports.
- We could treating special phrases like “first-quarter earnings report” as if they were single words, but a more principled approach is to introduce a new model, where each word is dependent on previous words.
- This model is in a sense perfectly “correct” in that it captures all possible interactions between words, but it is not practical: with a vocabulary of 100,000 words and a sentence length of 40, this model would have 10^200 parameters to estimate
- We can compromise with a Markov chain model that considers only the dependence between n adjacent words.
- **In an n-gram model, the probability of each word is dependent only on the n−1 previous words.**
### Other n-gram models
**character-level model**
- The probability of each character is determined by the n − 1 previous characters
- Helpful for dealing with unknown words, language identification
**skip-gram model**
- Count words that are near each other, but skip a word (or more) between them
### Smoothing n-gram models
- One way to model unknown words is to modify the training corpus by replacing infrequent words with a special symbol, traditionally `<UNK>`.
Still have a problem of unseen n-grams. -> Smoothing
- Backoff model: 
	- we start by estimating n-gram counts, but for any particular sequence that has a low (or zero) count, we back off to (n − 1)-grams.
	- Linear interpolation smoothing is a backoff model that combines trigram, bigram, and unigram models by linear interpolation
