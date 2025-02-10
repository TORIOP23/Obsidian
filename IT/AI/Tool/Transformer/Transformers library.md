# Pipeline function
![[pipeline.svg]]
## Tokenizer
- All this preprocessing needs to be done in exactly the same way as when the model was pretrained
![[tokenizer.png]]
```python
from transformers import AutoTokenizer

checkpoint = "distilbert-base-uncased-finetuned-sst-2-english"
tokenizer = AutoTokenizer.from_pretrained(checkpoint)
```
## Model 
```python
from transformers import AutoModel

checkpoint = "distilbert-base-uncased-finetuned-sst-2-english"
model = AutoModel.from_pretrained(checkpoint)
```
- For each model input, we’ll retrieve a high-dimensional vector representing the contextual understanding of that input by the Transformer model.
- While these hidden states can be useful on their own, they’re usually inputs to another part of the model, known as the **head**
### A high-dimensional vector
It generally has three dimensions:
- **Batch size**: The number of sequences processed at a time (2 in our example).
- **Sequence length**: The length of the numerical representation of the sequence (16 in our example).
- **Hidden size**: The vector dimension of each model input.
## Model heads: Making sense out of numbers
![[transformer_and_head.svg]]
- `*Model` (retrieve the hidden states)
- `*ForCausalLM`
- `*ForMaskedLM`
- `*ForMultipleChoice`
- `*ForQuestionAnswering`
- `*ForSequenceClassification`
- `*ForTokenClassification`
## Postprocessing the output
