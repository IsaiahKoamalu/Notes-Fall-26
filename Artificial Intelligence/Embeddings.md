- Why concatenate instead of sum/mean
	- keep order

#### Weight Tying
- Embedding matrix has shape(V, emb_dim)
- If last hidden layer of LM head is emb_dim then share the same parameters.

#### Word vectors
- Exhibit remarkable structure.
- high cosine similarity for similar words.
- word analogies for related words.
- Word to vec

#### Summary
- Cosine similarity
- Words (tokens) represented by dense vecotrs.
	- initialized randomly and learned through training.
	- emergent vector space structure.