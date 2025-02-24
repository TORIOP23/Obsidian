### bag-of-words model
- native Bayes model
- Imagine that for each category (business, weather, etc.) we have a bag full of words, the more common the word, the more slips it is duplicated on)
- To generate text, first select one of the bags and discard the others. Reach into that bag and pull out a word at random; this will be the first word of the sentence. Then put the word back and draw a second word. Repeat until an end-of-sentence indicator is drawn
- This model is clearly wrong
### N-gram word models
- The **bag-of-words** model has limitations. For example, the word “quarter” is common in both the business and sports categories. But the four-word sequence “first quarter earnings report” is common only in business and “fourth quarter touchdown passes” is common only in sports.
- We could treating special phrases like “first-quarter earnings report” as if they were single words, but a more principled approach is to introduce a new model, where each word is dependent on previous words.
- This model is in a sense perfectly “correct” in that it captures all possible interactions between words, but it is not practical: with a vocabulary of 100,000 words and a sentence length of 40, this model would have 10^200 parameters to estimate
- We can compromise with a Markov chain model that considers only the dependence between n adjacent words.
- In an n-gram model, the probability of each word is dependent only on the n−1 previous words.
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

### Word representation
- “a black cat” is valid because it follows a familiar pattern (article-adjective-noun), while “cat black a” does not
- The n-gram model misses this generalization because it is an atomic model: each word is an atom, distinct from every other word, with no internal structure
- One type of structured word model is a dictionary, usually constructed through manual labor. Example WordNet
### Part-of-speech (POS) tagging
- Category: noun, verb, adjective, and so on.
Common model for POS tagging is **hidden Markov model (HMM)**
- Takes in temporal sequence of evidence observations and predicts the most likely hidden states that could have produced that sequence.
- The evidence consisted of observations of a person carrying an umbrella (or not), and the hidden state was rain (or not) in the outside world.
- For POS tagging, the evidence is the sequence of words, W1:N, and the hidden states are the lexical categories, C1:N.
- The HMM is a generative model that says that the way to produce language is to start in one state, such as IN, the state for prepositions, and then make two choices: what word (such as from) should be emitted, and what state (such as DT) should come next. 
- The model does not consider any context other than the current part-of-speech state, nor does it have any idea of what the sentence is actually trying to convey. And yet it is a useful model—if we apply the **Viterbi algorithm** to find the most probable sequence of hidden states (tags), we find that the tagging achieves very high accuracy; usually around 97%
- HMM include transition model and sensor model
### Comparing language models 
- unigram (1-gram) is very poor approximation
- n-gram models - as n increases, they will produce language that is more fluent, but they tent to reproduce long passages from their training data verbatim (nguyên văn), rather than generate novel text 

# LLM
- Large Language Model
3 kind of LLM 
- Generic or raw language models
- Instruction-tuned language models
- Dialog-tuned language models
## [[Transformers]]
# Reference 
- [LLM](https://www.elastic.co/what-is/large-language-models)