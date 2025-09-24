# Query Expansion for Better Information Retrieval  

##  Project Overview  
When you look up for something in the search engines, the exact words you type may not match all the documents you’d actually find useful. For example:  
- Searching *“car accident”* might miss docs that only say *“traffic collision”* or *“road crash”*.  

To fix this, **query expansion system** was built.

In this .ipynb i built:
- It takes a user query  
- Finds semantically related terms using **Word2Vec embeddings**  
- Expands the query with those terms  
- Runs the expanded query through a **BM25-based retrieval system**  
- Ranks documents more effectively  

The result: **users get more complete and relevant search results** compared to the baseline.  

---

##  Steps :   

1. **Data Preprocessing**  
   - Tokenized queries and documents  
   - Removed stopwords and punctuation  
   - Applied lemmatization (reduced words to base form like *running → run*)  

2. **Trained Word Embeddings**  
   - Used **Word2Vec (Skip-Gram & CBOW)** on the document collection  
   - Generated vector representations of words so that similar words end up “close” in vector space  

3. **Query Expansion**  
   - For each query term, found its most similar words in the embedding space  
   - Added those related words back into the query  
   - Example:  
     ```
     "car accident" → "car accident, traffic collision, road crash, vehicle accident"
     ```

4. **Ranking**  
   - Used **BM25** (a classic ranking function) to score documents against both the original and expanded queries  
   - Compared performance to see if expansion really helped  

---

##  Results  
- **Baseline (no expansion):** Many relevant documents missed because of vocabulary mismatch  
- **With query expansion:** Noticeable improvements across retrieval metrics like **MAP** and **P@10**  
- **Best setting:** Skip-Gram embeddings + whole-query expansion + reweighting (give original terms more importance than expansion terms)  

 In plain terms: the system found **more relevant results without hurting precision**.  

---
