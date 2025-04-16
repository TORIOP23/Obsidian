- Named Entity Recognition
- Hello! I'm **MAX** ==PER== . I'd like to book a flight to **South Korea** ==LOC== .
# How NER model work
- **BIO** (Beginning, Inside, Outside)
It works by marking tokens
- “O” (i.e. “outside”) if they are not part of an entity
- “B-PER” (i.e. “beginning person”)
- “B-LOC” (i.e. “beginning location”) 
- “I-PER” (i.e. “inside person”)
- “I-LOC” (i.e. “inside location”)