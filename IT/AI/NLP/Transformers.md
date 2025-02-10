# Architecture
- Attention is all you need - 2017
![[transformer.png]]
## Encoder
### [[Word Embeddings]]
### Positional Encoding
- một từ ở vị trí khác nhau của câu lại mang ý nghĩa khác nhau
### Self-Attention
- cơ chế giúp Transformers "hiểu" được sự liên quan giữa các từ trong một câu. Ví dụ như từ "kicked" trong câu "I kicked the ball" (tôi đã đá quả bóng) liên quan như thế nào đến các từ khác?
### Multi-head Attention
### Residuals
### Feed Forward
## Decoder
### Masked Multi-head Attention
### Quá trình decode

# Transformer model
- [[Decoder models |GPT-like]] (also called _auto-regressive_ Transformer models)
- [[Encoder models|BERT-like]] (also called _auto-encoding_ Transformer models)
- [[Seq2seq|BART/T5-like]] (also called _sequence-to-sequence_ Transformer models)
How do Transformer work?
- They have been trained on large amounts of raw text in a [[Self-Supervised learning|self-supervised]] fashion.
- The general pretrained model then goes through a process called [[Transfer learning|transfer learning]]. During this process, the model is fine-tuned in a supervised way — that is, using human-annotated labels — on a given task.

# Reference 
- [Viblo](https://viblo.asia/p/transformers-nguoi-may-bien-hinh-bien-doi-the-gioi-nlp-924lJPOXKPM)