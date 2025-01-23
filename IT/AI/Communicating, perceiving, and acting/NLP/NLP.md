3 reasons for computers to do NLP
- To communicate with humans
- To lean 
- To advance the scientific understanding

- The process of dividing a text into a sequence of words is called tokenization
## [[Language Models ]]

## Grammar
- Set of rules that defines the tree structure of allowable phrases, 
- Idea: Hierarchical syntactic structure
**Probabilistic context-free grammar - PCFG** 
- "context-free" means that any rule can be used in any context. 
## Parsing
- Process of analyzing a string of words to uncover its phrase structure

- `Have the students in section 2 of Computer Science 101 take the exam.`
- `Have the students in section 2 of Computer Science 101 taken the exam?`
- A left-to-right parsing algorithm would have to guess whether the first word is part of a command or a question and will not be able to tell if the guess is correct until at least the eleventh word, take or taken. If the algorithm guesses wrong, it will have to backtrack all the way to the first word and reanalyze the whole sentence under the other interpretation.
- We can use **dynamic programming**: every time we analyze a substring, store the results so we won’t have to reanalyze it later.
- We can record the result in data structure known as a chart. An algorithm that does this is called a chart parser
- Chart parser 
	- CYK algorithm
## Augmented Grammars
## Complications of Real Natural Language
- Quantification
- Pragmatics , ...
## Natural Language Task
- Speech recognition
- Text-to-speech
- Machine translation
- Information extraction
- Information retrieval
- Question Answering

# [[Deep Learning for NLP]]

- [[LLM]]