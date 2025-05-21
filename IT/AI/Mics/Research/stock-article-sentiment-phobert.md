
|               |                                                                                                              |
| ------------- | ------------------------------------------------------------------------------------------------------------ |
| **Name**      | [Stock article title sentiment-based classification using PhoBERT](https://ceur-ws.org/Vol-3026/paper25.pdf) |
| **Task**      | NLP - Classification                                                                                         |
| **Published** | 2021                                                                                                         |
| **Model**     | PhoBERT                                                                                                      |
| **Accuracy**  | 93%                                                                                                          |
| **Label**     | `positive`, `negative`, `neutral`                                                                            |
| **Code**      | https://github.com/209sontung/Vietnamese-stock-article-classification                                        |
- Đăng trong CEUR-WS (viết tắt của **CEUR Workshop Proceedings**)
![[stock-sentiment-1.png]]
## Preprocessing
- Applied VnCoreNLP's NER to extract all the proper nouns and replace those words that signify location with the word ”loc” or ”name” for the organization name, stock code, or person’s name
## Training
- Optimizer: AdamW optimizer
- Batch size = 32
- 10 epochs
	- 5 epochs with learning rate  $\alpha=5e^{-6}$  
	- 5 epochs with learning rate  $\alpha=5e^{-7}$    
- Softmax classification layer (3 nodes)
## Data
- 1000 titles of financial articles taken from CafeF.vn
- Label with the help of experts
- 187 negative
- 248 neutral
- 565 positive
- Train/Validate/Test = 80/10/10
## Result
![[stock-sentiment-2.png]]