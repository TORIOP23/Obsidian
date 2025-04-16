- Term Frequency-Inverse Document Frequency
## How It Works
- **Term Frequency (TF)**: Measures how frequently a word appears in a document. It’s usually calculated as the number of word occurrences divided by the document’s total number of words.
- **Inverse Document Frequency (IDF)**: Measures how important a word is by determining how rare it is across all documents in the dataset. Words that appear in many documents get a lower score, while rare words get a higher score.
- The final score for each word in a document is the product of its TF and IDF values.
## Zip's law