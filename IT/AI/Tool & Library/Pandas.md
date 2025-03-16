###  2 Core Object
- **DataFrame** is a table
- **Series** is a list
### Indexing
- `loc` and `iloc` are row-first, column-second
- `iloc` : Index-based selection
- `loc`: Label-based selection
```python
reviews.iloc[0] # first row
reviews.iloc[:, 0] # first column
reviews.iloc[:3, 0] # 3 first rows with first column

reviews.loc[0, 'country']
```
