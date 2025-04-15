- Splitting text into meaningful units called _tokens_.
All this preprocessing needs to be done in exactly the same way as when the model was pretrained
![[tokenizer.png]]
## Word-based
## Character-based
## Subword tokenization
Subword tokenization algorithms rely on the principle that frequently used words should not be split into smaller subwords, but rare words should be decomposed into meaningful subwords.

## Other
- Byte-level [[BPE]], as used in GPT-2
- WordPiece, as used in BERT
- SentencePiece or Unigram, as used in several multilingual models
- VN: underthesea, pyvi, VNCoreNLP, RDRsegment, coccoc-tokenizer.