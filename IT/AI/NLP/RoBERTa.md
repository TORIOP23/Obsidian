Robustly Optimized BERT Pretraining Approach
- Giống hệt kiến trúc của [[BERT]]
## Dynamic Masking
- BERT dùng static masking
- From the BERT’s architecture we remember that during pretraining BERT performs language modeling by trying to predict a certain percentage of masked tokens. The problem with the original implementation is the fact that chosen tokens for masking for a given text sequence across different batches are sometimes the same.
- More precisely, the training dataset is duplicated 10 times, thus each sequence is masked only in 10 different ways. Keeping in mind that BERT runs 40 training epochs, each sequence with the same masking is passed to BERT four times. As researchers found, it is slightly better to use dynamic masking meaning that masking is generated uniquely every time a sequence is passed to BERT. Overall, this results in less duplicated data during the training giving an opportunity for a model to work with more various data and masking patterns.
## Removing the next sentence prediction

## Increasing batch size
- Tăng batch size, giảm learning rate, và training step
## BPE
- The original BERT uses a subword-level tokenization with the vocabulary size of 30K which is learned after input preprocessing and using several heuristics. 
- RoBERTa uses bytes instead of unicode characters as the base for subwords and expands the vocabulary size up to 50K without any preprocessing or input tokenization. 
- This results in 15M and 20M additional parameters for BERT base and BERT large models respectively. The introduced encoding version in RoBERTa demonstrates slightly worse results than before.
- Nevertheless, in the vocabulary size growth in RoBERTa allows to encode almost any word or subword without using the unknown token, compared to BERT. This gives a considerable advantage to RoBERTa as the model can now more fully understand complex texts containing rare words.