- Category: noun, verb, adjective, and so on.
##  HMM - hidden Markov model
- Takes in temporal sequence of evidence observations and predicts the most likely hidden states that could have produced that sequence.
- The evidence consisted of observations of a person carrying an umbrella (or not), and the hidden state was rain (or not) in the outside world.
- For POS tagging, the evidence is the sequence of words, W1:N, and the hidden states are the lexical categories, C1:N.
- The HMM is a generative model that says that the way to produce language is to start in one state, such as IN, the state for prepositions, and then make two choices: what word (such as from) should be emitted, and what state (such as DT) should come next. 
- The model does not consider any context other than the current part-of-speech state, nor does it have any idea of what the sentence is actually trying to convey. And yet it is a useful model—if we apply the **Viterbi algorithm** to find the most probable sequence of hidden states (tags), we find that the tagging achieves very high accuracy; usually around 97%
- HMM include transition model and sensor model